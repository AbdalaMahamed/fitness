<template>
  <section class="fitness-page">
    <h1>Fitness Exercises</h1>

    <div v-if="loading" class="loading">Loading exercises...</div>
    <div v-if="error" class="error">Failed to load exercises: {{ error }}</div>

    <ul v-if="exercises.length">
      <li v-for="exercise in exercises" :key="exercise.id" class="exercise-card">
        <h2>{{ exercise.name }}</h2>
        <p v-html="exercise.description"></p>
      </li>
    </ul>

    <div v-if="!loading && !error && exercises.length === 0">
      No exercises found.
    </div>
  </section>
</template>

<script>
export default {
  name: 'FitnessPage',
  data() {
    return {
      exercises: [],
      loading: false,
      error: null,
    };
  },
  methods: {
    async fetchExercises() {
      this.loading = true;
      this.error = null;

      try {
        // Wger API endpoint for exercises (English only, status=2 means verified)
        const response = await fetch(
          'https://wger.de/api/v2/exercise/?language=2&status=2&limit=10'
        );

        if (!response.ok) {
          throw new Error(`HTTP error! status: ${response.status}`);
        }

        const data = await response.json();
        this.exercises = data.results;
      } catch (err) {
        this.error = err.message || 'Unknown error';
      } finally {
        this.loading = false;
      }
    }
  },
  mounted() {
    this.fetchExercises();
  }
};
</script>

<style scoped>
.fitness-page {
  max-width: 800px;
  margin: 2rem auto;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  padding: 1rem;
}

.loading,
.error {
  text-align: center;
  font-weight: bold;
  margin: 1.5rem 0;
  color: #cc0000;
}

ul {
  list-style: none;
  padding: 0;
}

.exercise-card {
  background: #f0f8ff;
  border-radius: 10px;
  box-shadow: 0 2px 6px rgb(0 0 0 / 0.1);
  padding: 1rem 1.5rem;
  margin-bottom: 1.25rem;
}

.exercise-card h2 {
  margin: 0 0 0.5rem;
  color: #2c3e50;
}

.exercise-card p {
  margin: 0;
  color: #555;
  line-height: 1.4;
}
</style>
