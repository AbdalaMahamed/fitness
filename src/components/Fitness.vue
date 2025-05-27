<template>
  <section class="fitness-page">
    <h1>All Workouts</h1>

    <div class="body-part-buttons">
      <button
        v-for="part in bodyParts"
        :key="part.id"
        :class="{ active: selectedBodyPartId === part.id }"
        @click="selectBodyPart(part.id)"
      >
        {{ part.name }}
      </button>
    </div>

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
          @click="openVideo(exercise.video_url)"
          style="cursor: pointer;"
        />
        <p v-html="exercise.description"></p>
      </li>
    </ul>

    <div v-if="!loading && !error && workouts.length === 0">
      No workouts found.
    </div>

    <!-- Video modal -->
    <div v-if="showVideoModal" class="video-modal" @click.self="closeVideo">
      <div class="video-container">
        <button class="close-btn" @click="closeVideo">✕</button>
        <video
          :src="currentVideoUrl"
          controls
          autoplay
          style="max-width: 100%; border-radius: 8px;"
        ></video>
      </div>
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
      showVideoModal: false,
      currentVideoUrl: null,
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
        const response = await axios.get(
          `http://127.0.0.1:8000/api/workouts/body-part/${this.selectedBodyPartId}`
        );
        this.workouts = response.data || [];
      } catch (error) {
        this.error = "Failed to load workouts.";
        this.workouts = [];
      } finally {
        this.loading = false;
      }
    },
    selectBodyPart(id) {
      this.selectedBodyPartId = id;
      this.fetchWorkoutsByBodyPart();
    },
    openVideo(videoUrl) {
      this.currentVideoUrl = videoUrl;
      this.showVideoModal = true;
    },
    closeVideo() {
      this.showVideoModal = false;
      this.currentVideoUrl = null;
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
  text-align: center;
}

.body-part-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
  justify-content: center;
}

.body-part-buttons button {
  padding: 0.5rem 1rem;
  border: none;
  background-color: #1e3a8a;
  color: white;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.body-part-buttons button:hover {
  background-color: #3b82f6;
}

.body-part-buttons button.active {
  background-color: #2563eb;
  font-weight: bold;
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
  cursor: pointer;
}

/* Video Modal Styles */
.video-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 2000;
}

.video-container {
  position: relative;
  max-width: 800px;
  width: 90%;
  background: #000;
  padding: 1rem;
  border-radius: 10px;
}

.close-btn {
  position: absolute;
  top: 8px;
  right: 8px;
  background: transparent;
  border: none;
  color: #fff;
  font-size: 1.5rem;
  cursor: pointer;
  font-weight: bold;
  line-height: 1;
  padding: 0;
}
</style>
