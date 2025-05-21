<template>
  <section class="fitness-page">
    <h1>Workout Categories</h1>

    <div v-if="loadingCategories" class="loading">Loading categories...</div>
    <div v-if="errorCategories" class="error">{{ errorCategories }}</div>

    <ul v-if="!loadingCategories && !errorCategories" class="category-list">
      <li
        v-for="category in categories"
        :key="category.id"
        :class="{ selected: category.id === selectedCategoryId }"
        @click="selectCategory(category.id)"
      >
        {{ category.name }}
      </li>
    </ul>

    <div v-if="selectedCategoryId">
      <h2>Exercises for "{{ getCategoryName(selectedCategoryId) }}"</h2>

      <div v-if="loadingExercises" class="loading">Loading exercises...</div>
      <div v-if="errorExercises" class="error">{{ errorExercises }}</div>

      <ul v-if="!loadingExercises && !errorExercises && exercises.length" class="exercise-list">
        <li v-for="exercise in exercises" :key="exercise.id" class="exercise-card">
          <h3>{{ exercise.name }}</h3>
          <img
            v-if="exercise.images.length"
            :src="exercise.images[0].image"
            :alt="exercise.name"
            class="exercise-image"
          />
          <p v-html="exercise.description"></p>
        </li>
      </ul>

      <div v-if="!loadingExercises && !errorExercises && exercises.length === 0">
        No exercises found for this category.
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "WorkoutCategories",
  data() {
    return {
      categories: [],
      selectedCategoryId: null,
      exercises: [],
      loadingCategories: false,
      loadingExercises: false,
      errorCategories: null,
      errorExercises: null,
    };
  },
  methods: {
    async fetchCategories() {
      this.loadingCategories = true;
      this.errorCategories = null;
      try {
        const res = await fetch("https://wger.de/api/v2/exercisecategory/");
        if (!res.ok) throw new Error(`HTTP error! status: ${res.status}`);
        const data = await res.json();
        this.categories = data.results;
      } catch (e) {
        this.errorCategories = e.message || "Failed to load categories";
      } finally {
        this.loadingCategories = false;
      }
    },
    async fetchExercisesByCategory(categoryId) {
      this.loadingExercises = true;
      this.errorExercises = null;
      this.exercises = [];
      try {
        // Fetch exercises filtered by category, language=2 is English
        const res = await fetch(
          `https://wger.de/api/v2/exerciseinfo/?language=2&category=${categoryId}`
        );
        if (!res.ok) throw new Error(`HTTP error! status: ${res.status}`);
        const data = await res.json();
        this.exercises = data.results.filter(ex => ex.images && ex.images.length);
      } catch (e) {
        this.errorExercises = e.message || "Failed to load exercises";
      } finally {
        this.loadingExercises = false;
      }
    },
    selectCategory(categoryId) {
      this.selectedCategoryId = categoryId;
      this.fetchExercisesByCategory(categoryId);
    },
    getCategoryName(id) {
      const cat = this.categories.find(c => c.id === id);
      return cat ? cat.name : "";
    },
  },
  mounted() {
    this.fetchCategories();
  },
};
</script>

<style scoped>
.fitness-page {
  max-width: 800px;
  margin: 2rem auto;
  font-family: Arial, sans-serif;
  padding: 1rem;
  color: #222;
}

.loading,
.error {
  text-align: center;
  font-weight: bold;
  margin: 1.5rem 0;
  color: #d00;
}

.category-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.8rem;
  padding: 0;
  list-style: none;
  margin-bottom: 1.5rem;
}

.category-list li {
  cursor: pointer;
  padding: 0.6rem 1.2rem;
  background: #ddd;
  border-radius: 20px;
  user-select: none;
  transition: background-color 0.3s ease;
}

.category-list li.selected,
.category-list li:hover {
  background: #4f46e5;
  color: white;
}

.exercise-list {
  list-style: none;
  padding: 0;
}

.exercise-card {
  background: #eef6ff;
  border-radius: 8px;
  padding: 1rem 1.5rem;
  margin-bottom: 1.5rem;
  box-shadow: 0 2px 5px rgb(0 0 0 / 0.1);
}

.exercise-card h3 {
  margin: 0 0 0.5rem;
  color: #1e3a8a;
}

.exercise-image {
  max-width: 100%;
  height: auto;
  border-radius: 6px;
  margin-bottom: 1rem;
}

.exercise-card p {
  margin: 0.5rem 0;
  line-height: 1.4;
}
</style>
