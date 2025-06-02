<template>
  <div>
    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-overlay">
        <h1>Unleash Your Potential</h1>
        <p class="sub">Transform your body and mind with expert coaching and customized fitness plans.</p>
        <button @click="scrollToWorkout">Get Started</button>
      </div>
    </section>

    <!-- Program Features Grid -->
    <section class="features">
      <h2>What We Offer</h2>
      <div class="grid">
        <div class="feature-card">
          <img src="https://img.icons8.com/ios-filled/100/weightlifting.png" alt="Strength" />
          <h3>Strength Training</h3>
          <p>Build muscle, gain strength, and increase endurance with personalized programs.</p>
        </div>
        <div class="feature-card">
          <img src="https://img.icons8.com/ios-filled/100/apple.png" alt="Nutrition" />
          <h3>Nutrition Coaching</h3>
          <p>Learn what to eat and when. Tailored meal plans that match your fitness goals.</p>
        </div>
        <div class="feature-card">
          <img src="https://img.icons8.com/ios-filled/100/yoga.png" alt="Mobility" />
          <h3>Mobility & Recovery</h3>
          <p>Stay flexible, injury-free, and optimize performance with smart recovery routines.</p>
        </div>
      </div>
    </section>

    <!-- Training Preview -->
    <section id="workout" class="training-preview">
      <div class="text">
        <h2>Start Your Journey Today</h2>
        <p>
          Whether you're new to training or a seasoned athlete, we’ll guide you to your goals with science-backed techniques and accountability.
        </p>
        <button @click="$emit('navigate', 'fitness')">See Fitness Plans</button>
      </div>
      <iframe class="video" src="https://www.youtube.com/shorts/PPmvh7gBTi0" title="Workout intro" frameborder="0" allowfullscreen></iframe>
    </section>

    <!-- Testimonials -->
    <section class="testimonials">
      <h2>What Members Say</h2>
      <div class="cards">
        <div class="card">
          <p>“Down 8kg and stronger than ever. The trainers here care and it shows.”</p>
          <h4>- Jamie R.</h4>
        </div>
        <div class="card">
          <p>“I actually look forward to working out now. The results speak for themselves.”</p>
          <h4>- Lina K.</h4>
        </div>
        <div class="card">
          <p>“Nutrition + training = results. Best decision I made this year.”</p>
          <h4>- David M.</h4>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'FitnessHome',
  methods: {
    scrollToWorkout() {
      const el = document.getElementById('workout');
      if (el) {
        el.scrollIntoView({ behavior: 'smooth' });
      }
    },
  },
};
</script>

<style scoped>
/* Hero Section */
.hero {
  background: url('https://images.unsplash.com/photo-1558611848-73f7eb4001a1?auto=format&fit=crop&w=1600&q=80') no-repeat center center/cover;
  height: 90vh;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}
.hero-overlay {
  background-color: rgba(0, 0, 0, 0.6);
  color: white;
  padding: 2rem;
  border-radius: 1rem;
  text-align: center;
  max-width: 90%;
}
.hero-overlay h1 {
  font-size: 3rem;
  margin-bottom: 0.5rem;
}
.hero-overlay .sub {
  font-size: 1.2rem;
  margin-bottom: 1.5rem;
}
.hero-overlay button {
  background-color: #e11d48;
  color: white;
  padding: 0.8rem 2rem;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  cursor: pointer;
}
.hero-overlay button:hover {
  background-color: #be123c;
}

/* Features Section */
.features {
  background-color: #f1f5f9;
  padding: 3rem 2rem;
  text-align: center;
}
.features h2 {
  font-size: 2rem;
  margin-bottom: 2rem;
}
.grid {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  justify-content: center;
}
.feature-card {
  background: white;
  border-radius: 1rem;
  padding: 2rem;
  width: 250px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}
.feature-card img {
  width: 50px;
  margin-bottom: 1rem;
}
.feature-card h3 {
  margin-bottom: 0.5rem;
  color: #1e293b;
}
.feature-card p {
  color: #4b5563;
  font-size: 0.95rem;
}

/* Training Preview */
.training-preview {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 2rem;
  padding: 4rem 2rem;
}
.training-preview .text {
  flex: 1 1 400px;
}
.training-preview h2 {
  font-size: 1.8rem;
  margin-bottom: 1rem;
}
.training-preview p {
  font-size: 1.1rem;
  margin-bottom: 1.5rem;
}
.training-preview button {
  background-color: #0f172a;
  color: white;
  padding: 0.8rem 1.5rem;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}
.video {
  flex: 1 1 400px;
  width: 100%;
  height: 250px;
  border-radius: 1rem;
}

/* Testimonials */
.testimonials {
  background: #f9fafb;
  padding: 3rem 2rem;
  text-align: center;
}
.testimonials h2 {
  margin-bottom: 2rem;
}
.cards {
  display: flex;
  gap: 2rem;
  flex-wrap: wrap;
  justify-content: center;
}
.card {
  background: white;
  padding: 2rem;
  border-radius: 1rem;
  max-width: 300px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.05);
}
.card p {
  font-style: italic;
  margin-bottom: 1rem;
}
.card h4 {
  color: #1f2937;
}

/* Responsive */
@media (max-width: 768px) {
  .training-preview {
    flex-direction: column;
  }
  .grid {
    flex-direction: column;
    align-items: center;
  }
  .video {
    height: 200px;
  }
}
</style>
