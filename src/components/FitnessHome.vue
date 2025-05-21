<template>
  <div>
    <!-- Hero Section -->
    <section class="hero-image" style="background-image: url('/assets/your-image.jpg')">
      <div class="overlay">
        <h1>Welcome to WORK</h1>
        <p>Premium Personal Training Health Club in the heart of Strijp-S Eindhoven</p>
        <button @click="$emit('navigate', 'fitness')">Start Training</button>
      </div>
    </section>

    <!-- Club Section -->
    <section class="split-section">
      <img src="https://static.wixstatic.com/media/80cc9e_2be2c18e9df849d5bbb73f2095af1f1f~mv2.jpg/v1/fill/w_1901,h_880,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/80cc9e_2be2c18e9df849d5bbb73f2095af1f1f~mv2.jpg" alt="Club Image" />
      <div class="text">
        <h3>A Club Designed for You</h3>
        <p>We built a club for EVERYONE. Fun, inviting, a little chic. Skip the big gym hassles. Enjoy the luxury of a personalized space.</p>
        <button @click="$emit('navigate', 'club')">See the Club</button>
      </div>
    </section>

    <!-- Training Section -->
    <section class="split-section reverse">
      <img src="https://assets-us-01.kc-usercontent.com/a07c5ec0-e08a-0014-c8c5-a7a73768c21f/d88f6bc9-3495-4e04-87d3-17fd6ce3e38e/TrainingFundamentals2-954x534.jpg" alt="Training Image" />
      <div class="text">
        <h3>Training for Your Style</h3>
        <p>Get a personal plan and expert coaching that pushes your limits. Our approach keeps you inspired and progressing.</p>
        <button @click="$emit('navigate', 'fitness')">See Training</button>
      </div>
    </section>

    <!-- Testimonials Section -->
    <section class="testimonials-section">
      <h2>What Our Members Say</h2>
      <div class="testimonials-container">
        <div class="testimonial">
          <p>"The trainers here truly care about your progress. Best gym experience ever!"</p>
          <h4>- Alex P.</h4>
        </div>
        <div class="testimonial">
          <p>"I love the personalized plans and the supportive community."</p>
          <h4>- Maria S.</h4>
        </div>
        <div class="testimonial">
          <p>"Facilities are clean and welcoming, with a great atmosphere."</p>
          <h4>- John D.</h4>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'FitnessHome',
}
</script>

<style scoped>
body {
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #ffffff;
  color: #111;
}

.hero-image,
.full-image {
  width: 100%;
  height: 100vh;
  background-size: cover;
  background-position: center;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}

.hero-image .overlay {
  background-color: rgba(0, 0, 0, 0.5);
  padding: 3rem;
  border-radius: 12px;
  color: white;
  text-align: center;
}

.hero-image .overlay h1 {
  font-size: 3.5rem;
  margin-bottom: 1rem;
}

.hero-image .overlay p {
  font-size: 1.3rem;
  margin-bottom: 2rem;
}

.hero-image .overlay button {
  background-color: #d10505;
  border: none;
  padding: 1rem 2.5rem;
  font-size: 1.2rem;
  color: white;
  border-radius: 8px;
  cursor: pointer;
  transition: 0.3s ease;
}
.hero-image .overlay button:hover {
  background-color: #a00303;
}

.split-section {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  align-items: center;
  margin: 4rem auto;
  max-width: 1200px;
  padding: 2rem;
}
.split-section.reverse {
  flex-direction: row-reverse;
}
.split-section img {
  flex: 1 1 50%;
  max-width: 100%;
  border-radius: 12px;
}
.split-section .text {
  flex: 1 1 50%;
}
.split-section .text h3 {
  font-size: 2rem;
  margin-bottom: 1rem;
}
.split-section .text p {
  font-size: 1.1rem;
  color: #444;
  line-height: 1.6;
}
.split-section .text button {
  margin-top: 1rem;
  background: #d10505;
  color: white;
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 6px;
  font-size: 1rem;
  cursor: pointer;
}
.split-section .text button:hover {
  background: #a00303;
}

/* Testimonials Section */
.testimonials-section {
  background: #f7f7f7;
  padding: 4rem 2rem;
  text-align: center;
  max-width: 900px;
  margin: 4rem auto;
  border-radius: 12px;
}

.testimonials-section h2 {
  font-size: 2.5rem;
  margin-bottom: 2rem;
  color: #d10505;
}

.testimonials-container {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  justify-content: center;
}

.testimonial {
  background: white;
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgb(0 0 0 / 0.1);
  flex: 1 1 250px;
  max-width: 300px;
}

.testimonial p {
  font-style: italic;
  color: #555;
  margin-bottom: 1rem;
}

.testimonial h4 {
  font-weight: 600;
  color: #333;
}

/* Responsive */
@media (max-width: 768px) {
  .hero-image .overlay h1 {
    font-size: 2.2rem;
  }
  .split-section {
    flex-direction: column;
  }
  .testimonials-container {
    flex-direction: column;
  }
}
</style>
