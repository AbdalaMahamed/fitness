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
  metaInfo() {
    return {
      title: 'All Workouts | YourSiteName',
      meta: [
        {
          name: 'description',
          content: 'Browse workouts by body part to build muscle, lose fat, and improve fitness. Video tutorials included.'
        },
        {
          name: 'keywords',
          content: 'workouts, fitness, muscle building, fat loss, body parts, exercise videos'
        },
        {
          property: 'og:title',
          content: 'All Workouts | YourSiteName'
        },
        {
          property: 'og:description',
          content: 'Browse workouts by body part to build muscle, lose fat, and improve fitness. Video tutorials included.'
        },
        {
          property: 'og:type',
          content: 'website'
        }
      ]
    };
  },
};
</script>

<style scoped>
.fitness-page {
  max-width: 1400px;
  margin: 2rem auto;
  padding: 2rem;
  font-family: 'Poppins', sans-serif;
  color: #ffffff;
  background-color: #0f0f0f;
  text-align: center;
  animation: fadeIn 0.6s ease-in-out;
}

h1 {
  font-size: 3rem;
  font-weight: 700;
  color: #ffffff;
  margin-bottom: 2rem;
  letter-spacing: 1px;
  text-transform: uppercase;
  border-bottom: 2px solid #ffffff20;
  display: inline-block;
  padding-bottom: 0.5rem;
}

.body-part-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
  margin-bottom: 2.5rem;
}

.body-part-buttons button {
  padding: 0.75rem 1.5rem;
  background-color: #1a1a1a;
  color: #ffffff;
  border: 1px solid #ffffff30;
  border-radius: 999px;
  cursor: pointer;
  font-size: 1rem;
  font-weight: 600;
  transition: all 0.3s ease;
  white-space: nowrap;
}

.body-part-buttons button:hover {
  background-color: #ffffff10;
  border-color: #ffffff60;
}

.body-part-buttons button.active {
  background-color: #ffffff20;
  border-color: #ffffff80;
  box-shadow: 0 0 10px #ffffff30;
}

.loading,
.error {
  font-size: 1.2rem;
  font-weight: 600;
  color: #e5e5e5;
  margin: 2rem 0;
}

.exercise-list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
  padding: 0;
  list-style: none;
  justify-items: center;
}

.exercise-card {
  background: #1a1a1a;
  border-radius: 16px;
  padding: 1.5rem;
  box-shadow: 0 8px 20px rgba(255, 255, 255, 0.05);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  text-align: left;
  border: 1px solid #2a2a2a;
}

.exercise-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 28px rgba(255, 255, 255, 0.1);
}

.exercise-card h3 {
  font-size: 1.4rem;
  color: #ffffff;
  margin-top: 0;
}

.exercise-image {
  width: 100%;
  height: 240px;
  object-fit: cover;
  border-radius: 12px;
  border: 2px solid #333;
  margin: 1rem 0;
  transition: transform 0.3s ease;
  cursor: pointer;
  filter: grayscale(100%) brightness(0.9);
}

.exercise-image:hover {
  transform: scale(1.03);
  filter: grayscale(0%) brightness(1);
}

/* Video Modal */
.video-modal {
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.9);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 2000;
  animation: fadeIn 0.3s ease-in-out;
}

.video-container {
  position: relative;
  max-width: 900px;
  width: 90%;
  background: #000;
  border-radius: 16px;
  padding: 1rem;
  box-shadow: 0 0 40px rgba(255, 255, 255, 0.2);
}

.close-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  background: transparent;
  border: none;
  color: white;
  font-size: 2rem;
  font-weight: bold;
  cursor: pointer;
  z-index: 10;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Responsive voor tablets en mobiel */
@media (max-width: 1024px) {
  .exercise-list {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .exercise-list {
    grid-template-columns: 1fr;
  }

  .body-part-buttons {
    justify-content: center;
    gap: 0.5rem;
  }

  .body-part-buttons button {
    padding: 0.5rem 1rem;
    font-size: 0.9rem;
  }
}
</style>
