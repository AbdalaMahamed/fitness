<template>
  <div class="home">
    <!-- Hero Section -->
    <section class="hero">
      <video autoplay muted loop playsinline class="hero-video">
        <source :src="videoSrc" type="video/mp4" />
        Your browser does not support the video tag.
      </video>
      <div class="overlay">
        <h1>Unleash Your Potential</h1>
        <p>Unlock your full potential with science-backed workouts and expert coaching tailored to your goals.</p>
        <button @click="$emit('navigate', 'fitness')">See Fitness Plans</button>
      </div>
    </section>

    <!-- Programs Section -->
    <section id="programs" class="programs">
      <h2>What We Offer</h2>
      <div class="cards">
        <div class="card" v-for="program in programs" :key="program.title">
          <img :src="program.icon" :alt="program.title" />
          <h3>{{ program.title }}</h3>
          <p>{{ program.description }}</p>
        </div>
      </div>
    </section>

    <!-- Most Popular Section -->
    <section class="most-popular">
      <h2>Most Popular</h2>
      <div class="popular-cards">
        <div class="popular-card" v-for="program in mostPopularPrograms" :key="program.title">
          <div class="tag" v-if="program.tag">{{ program.tag }}</div>
          <h3>{{ program.title }}</h3>
          <p v-if="program.subtitle">{{ program.subtitle }}</p>
          <p class="experience">{{ program.experience }}</p>
          <p class="price">Sale price {{ program.price }}</p>
        </div>
      </div>
    </section>

    <!-- Training Programs & Nutrition Plan Section -->
    <section class="info-sections">
      <div class="info-card">
        <h3>Training Programs</h3>
        <p>World-Class training programs backed by science-based evidence</p>
        <button @click="goToFitness">Learn More</button>
      </div>
      <div class="info-card">
        <h3>Nutrition Plan</h3>
        <p>15 Chapters and over 250 pages of nutrition knowledge</p>
        <button @click="$emit('navigate', 'nutrition')">Learn More</button>
      </div>
    </section>

    <!-- Video Preview Section -->
    <section class="video-preview">
      <div class="text-content">
        <h2>Start Your Journey Today</h2>
        <p>Whether you're new to training or a seasoned athlete, we guide you with science-backed techniques.</p>
        <button @click="$emit('navigate', 'fitness')">See Fitness Plans</button>
      </div>
     <img src="https://www.gymshark.com/_next/image?url=https%3A%2F%2Fimages.ctfassets.net%2F8urtyqugdt2l%2Fn7bsM6FNEiiN1S112o654%2F03a8e2a49b9a401f4b26f5823b6b11b9%2Fmobile-jamal-browner-deadlift.jpg&w=3840&q=85" alt="">
      
      
    </section>

    <!-- ✅ BMR Calculator Section -->
    <section class="bmr-section">
      <h2>Calculate Your BMR</h2>
      <form @submit.prevent="calculateBMR">
        <div class="form-group">
          <label>Age</label>
          <input type="number" v-model.number="age" required />
        </div>
        <div class="form-group">
          <label>Gender</label>
          <select v-model="gender" required>
            <option value="">Select</option>
            <option value="male">Male</option>
            <option value="female">Female</option>
          </select>
        </div>
        <div class="form-group">
          <label>Height (cm)</label>
          <input type="number" v-model.number="height" required />
        </div>
        <div class="form-group">
          <label>Weight (kg)</label>
          <input type="number" v-model.number="weight" required />
        </div>
        <button type="submit">Calculate</button>
      </form>
      <div v-if="bmr !== null" class="bmr-result">
        <p>Your BMR is <strong>{{ bmr }}</strong> calories/day</p>
      </div>
    </section>
  </div>
</template>

<script>
import heroVideo from '@/assets/homepagevideo.mp4'
import previewVideo from '@/assets/homepagevideo.mp4'

export default {
  name: 'FitnessHome',
  data() {
    return {
      videoSrc: heroVideo,
      previewVideoSrc: previewVideo,
      age: null,
      gender: '',
      height: null,
      weight: null,
      bmr: null,
      programs: [
        {
          icon: 'https://img.icons8.com/ios-filled/50/weightlifting.png',
          title: 'Strength Training',
          description: 'Build muscle, gain strength, and increase endurance with personalized programs.'
        },
        {
          icon: 'https://img.icons8.com/ios-filled/50/apple.png',
          title: 'Nutrition Coaching',
          description: 'Tailored meal plans that match your fitness goals.'
        },
        {
          icon: 'https://img.icons8.com/ios-filled/50/yoga.png',
          title: 'Mobility & Recovery',
          description: 'Stay flexible and injury-free with smart recovery routines.'
        }
      ],
      mostPopularPrograms: [
        {
          title: 'The Bodybuilding Transformation System',
          tag: 'NEW',
          experience: 'All Experience Levels',
          price: '$49.99',
        },
        {
          title: 'The Pure Bodybuilding Program - Phase 2',
          subtitle: 'Wolf Rep Fitness',
          experience: 'Intermediate - Advanced',
          price: '$49.99',
        },
        {
          title: 'The Pure Bodybuilding Program',
          subtitle: 'Wolf Rep Fitness',
          experience: 'Intermediate - Advanced',
          price: '$49.99',
        },
        {
          title: 'The Essentials Program',
          subtitle: 'Wolf Rep Fitness',
          experience: 'All Experience Levels',
          price: '$39.99',
        },
        {
          title: 'Fundamentals Hypertrophy Program',
          subtitle: 'Wolf Rep Fitness',
          experience: 'Beginner - Intermediate',
          price: '$39.99',
        },
      ],
    };
  },
  methods: {
    scrollToSection(id) {
      const el = document.getElementById(id);
      if (el) el.scrollIntoView({ behavior: 'smooth' });
    },
    calculateBMR() {
      if (this.gender === 'male') {
        this.bmr = Math.round(10 * this.weight + 6.25 * this.height - 5 * this.age + 5);
      } else if (this.gender === 'female') {
        this.bmr = Math.round(10 * this.weight + 6.25 * this.height - 5 * this.age - 161);
      } else {
        this.bmr = null;
      }
    },
    goToFitness() {
      this.$router.push({ name: 'Fitness' }); // Make sure your route name is 'Fitness'
    },
    goToTrainingPrograms() {
      this.$router.push({ name: 'TrainingPrograms' }); // Adjust route name accordingly
    },
    goToNutritionPlan() {
      this.$router.push({ name: 'NutritionPlan' }); // Adjust route name accordingly
    }
  }
}
</script>

<style scoped>
.home {
  font-family: 'Poppins', sans-serif;
  color: #1e293b;
}

/* Hero Section */
.hero {
  position: relative;
  height: 100vh;
  overflow: hidden;
}
.hero-video {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: 0;
}
.overlay {
  position: relative;
  z-index: 1;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: white;
  background: rgba(0, 0, 0, 0.4);
  padding: 0 2rem;
}
.overlay h1 {
  font-size: 4rem;
  margin-bottom: 1rem;
  font-weight: 700;
  text-shadow: 0 0 12px rgba(0,0,0,0.7);
}
.overlay p {
  font-size: 1.5rem;
  margin-bottom: 2rem;
  max-width: 600px;
  text-shadow: 0 0 8px rgba(0,0,0,0.7);
}
.overlay button {
  background: #e11d48;
  border: none;
  padding: 1rem 2.5rem;
  color: white;
  font-weight: 600;
  font-size: 1.1rem;
  border-radius: 9999px;
  cursor: pointer;
  transition: background 0.3s ease;
}
.overlay button:hover {
  background: #be123c;
}

/* Programs Section */
.programs {
  padding: 4rem 2rem;
  text-align: center;
  background: #f9fafb;
}
.programs h2 {
  font-size: 2.5rem;
  margin-bottom: 3rem;
}
.cards {
  display: flex;
  justify-content: center;
  gap: 3rem;
  flex-wrap: wrap;
}
.card {
  background: white;
  padding: 2.5rem 2rem;
  border-radius: 1rem;
  width: 280px;
  box-shadow: 0 6px 15px rgb(0 0 0 / 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: default;
  user-select: none;
}
.card:hover {
  transform: translateY(-10px);
  box-shadow: 0 15px 30px rgb(0 0 0 / 0.15);
}
.card img {
  width: 50px;
  margin-bottom: 1.5rem;
}
.card h3 {
  font-weight: 700;
  margin-bottom: 1rem;
  font-size: 1.3rem;
}
.card p {
  color: #475569;
  font-size: 1rem;
  line-height: 1.4;
}

/* Most Popular Section */
.most-popular {
  padding: 4rem 2rem;
  background: #fff7f7;
  text-align: center;
}
.most-popular h2 {
  font-size: 2.5rem;
  margin-bottom: 2.5rem;
  color: #e11d48;
}
.popular-cards {
  display: flex;
  justify-content: center;
  gap: 2rem;
  flex-wrap: wrap;
}
.popular-card {
  background: white;
  border-radius: 1rem;
  padding: 1.8rem 2rem;
  width: 260px;
  box-shadow: 0 6px 15px rgba(0,0,0,0.08);
  text-align: left;
  position: relative;
  cursor: default;
}
.popular-card .tag {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: #e11d48;
  color: white;
  padding: 0.25rem 0.7rem;
  font-weight: 700;
  font-size: 0.85rem;
  border-radius: 6px;
  user-select: none;
}
.popular-card h3 {
  font-size: 1.25rem;
  margin-bottom: 0.4rem;
  font-weight: 700;
  color: #1e293b;
}
.popular-card p {
  margin: 0.2rem 0;
  color: #475569;
}
.popular-card .experience {
  font-style: italic;
  color: #64748b;
}
.popular-card .price {
  font-weight: 700;
  color: #e11d48;
  margin-top: 0.8rem;
}

/* Info Sections */
.info-sections {
  display: flex;
  justify-content: center;
  gap: 3rem;
  padding: 3rem 2rem;
  max-width: 900px;
  margin: 0 auto 4rem;
  flex-wrap: wrap;
}
.info-card {
  background: #fef3f3;
  padding: 2rem;
  border-radius: 1rem;
  flex: 1 1 300px;
  box-shadow: 0 6px 15px rgba(225, 29, 72, 0.2);
  text-align: center;
}
.info-card h3 {
  color: #e11d48;
  font-size: 1.8rem;
  margin-bottom: 1rem;
  font-weight: 700;
}
.info-card p {
  font-size: 1.1rem;
  margin-bottom: 1.5rem;
  color: #334155;
}
.info-card button {
  background: #e11d48;
  color: white;
  border: none;
  padding: 0.75rem 2rem;
  border-radius: 9999px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.3s ease;
}
.info-card button:hover {
  background: #be123c;
}

/* Video Preview Section */
.video-preview {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 3rem 2rem;
  gap: 3rem;
  flex-wrap: wrap;
  background: #f9fafb;
}
.text-content {
  max-width: 400px;
}
.text-content h2 {
  font-size: 2rem;
  margin-bottom: 1rem;
  color: #1e293b;
}
.text-content p {
  font-size: 1.1rem;
  margin-bottom: 2rem;
  color: #475569;
}
.text-content button {
  background: #e11d48;
  color: white;
  border: none;
  padding: 0.8rem 2rem;
  border-radius: 9999px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.3s ease;
}
.text-content button:hover {
  background: #be123c;
}
.preview-video {
  max-width: 450px;
  border-radius: 1rem;
  box-shadow: 0 6px 15px rgba(0,0,0,0.1);
}

/* BMR Section */
.bmr-section {
  max-width: 500px;
  margin: 0 auto 5rem;
  padding: 2rem;
  background: #fff7f7;
  border-radius: 1rem;
  box-shadow: 0 6px 15px rgba(225, 29, 72, 0.2);
  text-align: center;
}
.bmr-section h2 {
  color: #e11d48;
  margin-bottom: 1.5rem;
}
.form-group {
  margin-bottom: 1rem;
  text-align: left;
}
.form-group label {
  display: block;
  margin-bottom: 0.3rem;
  font-weight: 600;
  color: #475569;
}
.form-group input,
.form-group select {
  width: 100%;
  padding: 0.6rem;
  border-radius: 0.5rem;
  border: 1px solid #cbd5e1;
  font-size: 1rem;
}
.bmr-section button {
  background: #e11d48;
  color: white;
  border: none;
  padding: 0.8rem 3rem;
  border-radius: 9999px;
  font-weight: 700;
  cursor: pointer;
  margin-top: 1rem;
  transition: background 0.3s ease;
}
.bmr-section button:hover {
  background: #be123c;
}
.bmr-result {
  margin-top: 1.5rem;
  font-size: 1.3rem;
  font-weight: 600;
  color: #1e293b;
}

/* Responsive */
@media (max-width: 768px) {
  .cards,
  .popular-cards {
    flex-direction: column;
    align-items: center;
  }
  .info-sections {
    flex-direction: column;
  }
  .video-preview {
    flex-direction: column;
  }
  .preview-video {
    max-width: 100%;
  }
}
</style>
