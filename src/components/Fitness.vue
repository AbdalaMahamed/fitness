  <template>
    <section class="fitness-page">
      <h1>All Workouts</h1>

      <label for="bodyPartSelect">Select Body Part:</label>
      <select id="bodyPartSelect" v-model="selectedBodyPartId" @change="fetchWorkoutsByBodyPart">
        <option disabled value="">-- Choose a body part --</option>
        <option v-for="part in bodyParts" :key="part.id" :value="part.id">
          {{ part.name }}
        </option>
      </select>

      <div v-if="loading" class="loading">Loading workouts...</div>
      <div v-if="error" class="error">{{ error }}</div>

      <ul v-if="!loading && !error && workouts.length" class="exercise-list">
        <li v-for="exercise in workouts" :key="exercise.id" class="exercise-card">
          <h3>{{ exercise.name }}</h3>
          <img
            v-if="exercise.image_url"
            :src="exercise.image_url"
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
    name: "FitnessPage",
    data() {
      return {
        workouts: [],
        bodyParts: [],
        selectedBodyPartId: "",
        loading: false,
        error: null,
      };
    },
    methods: {
      async fetchBodyParts() {
        try {
          const response = await axios.get("http://127.0.0.1:8000/api/body-parts");
          this.bodyParts = response.data;
        } catch (error) {
          this.error = "Failed to load body parts.";
        }
      },
      async fetchWorkoutsByBodyPart() {
        if (!this.selectedBodyPartId) return;
        this.loading = true;
        this.error = null;
        try {
          const response = await axios.get(`http://127.0.0.1:8000/api/workouts/body-part/${this.selectedBodyPartId}`);
          this.workouts = response.data || [];
        } catch (error) {
          this.error = "Failed to load workouts.";
          this.workouts = [];
        } finally {
          this.loading = false;
        }
      },
    },
    mounted() {
      this.fetchBodyParts();
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

  label {
    font-weight: bold;
    margin-right: 0.5rem;
  }

  select {
    padding: 0.5rem;
    font-size: 1rem;
    margin-bottom: 1rem;
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
