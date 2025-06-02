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
            v-if="exercise.images && exercise.images.length"
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
import axios from "axios";

export default {
  name: "WorkoutCategories",
  data() {
    return {
      apiBaseUrl: "http://your-laravel-api-domain/api", // Change to your Laravel API base URL
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
        const response = await axios.get(`${this.apiBaseUrl}/body-parts`);
        // Assuming response.data contains array of categories
        this.categories = response.data;
      } catch (error) {
        this.errorCategories = error.response?.data?.message || error.message || "Failed to load categories";
      } finally {
        this.loadingCategories = false;
      }
    },
    async fetchExercisesByCategory(categoryId) {
      this.loadingExercises = true;
      this.errorExercises = null;
      this.exercises = [];
      try {
        const response = await axios.get(`${this.apiBaseUrl}/workouts/body-part/${categoryId}`);
        // Assuming response.data contains array of exercises
        this.exercises = response.data;
      } catch (error) {
        this.errorExercises = error.response?.data?.message || error.message || "Failed to load exercises";
      } finally {
        this.loadingExercises = false;
      }
    },
    selectCategory(categoryId) {
      this.selectedCategoryId = categoryId;
      this.fetchExercisesByCategory(categoryId);
    },
    getCategoryName(id) {
      const cat = this.categories.find((c) => c.id === id);
      return cat ? cat.name : "";
    },
  },
  mounted() {
    this.fetchCategories();
  },
};
</script>

<style scoped>
/* Your existing styles here */
</style>
