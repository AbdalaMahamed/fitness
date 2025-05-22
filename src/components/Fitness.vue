<template>
  <section class="fitness-page">
    <h1>All Workouts</h1>

    <div v-if="loading" class="loading">Loading workouts...</div>
    <div v-if="error" class="error">{{ error }}</div>

    <ul v-if="!loading && !error && workouts.length" class="exercise-list">
      <li v-for="exercise in workouts" :key="exercise.id" class="exercise-card">
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

    <div v-if="!loading && !error && workouts.length === 0">
      No workouts found.
    </div>
  </section>
</template>

<script>
import axios from "axios";

export default {
  name: "FitnessPage",  // Naam aangepast naar 'Fitness' hier
  data() {
    return {
      workouts: [],
      loading: false,
      error: null,
    };
  },
  methods: {
    async fetchWorkouts() {
      this.loading = true;
      this.error = null;
      try {
        const response = await axios.get("http://127.0.0.1:8000/api/workouts");
        this.workouts = response.data;
      } catch (error) {
        this.error = error.response?.data?.message || error.message || "Failed to load workouts";
      } finally {
        this.loading = false;
      }
    },
  },
  mounted() {
    this.fetchWorkouts();
  },
};
</script>

<style scoped>
.fitness-page {
  max-width: 1000px;
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

.exercise-list {
  padding: 0;
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
}

.exercise-card {
  background: #eef6ff;
  border-radius: 8px;
  padding: 1rem;
  width: 100%;
  max-width: 300px;
  box-shadow: 0 2px 5px rgb(0 0 0 / 0.1);
  box-sizing: border-box;
}

.exercise-card h3 {
  margin-top: 0;
  color: #1e3a8a;
  font-size: 1.1rem;
}

.exercise-image {
  width: 90px;
  height: 90px;
  object-fit: cover;
  border-radius: 6px;
  border: 1px solid #ccc;
  margin: 0.5rem 0;
}
</style>
