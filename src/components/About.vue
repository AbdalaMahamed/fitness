<template>
  <section class="about-modern">
    <div class="text-section">
      <h1 class="title">Welcome to <span class="gradient-text">FitNova</span></h1>
      <p>
        At FitNova, we redefine fitness. It’s not just about reps and sets — it's about balance, mindset, and a powerful community.
      </p>
      <p>
        With science-backed workouts, smart nutrition advice, and real transformation stories, we help you become your best self — one day at a time.
      </p>
      <p>
        Whether you’re starting your journey or breaking limits, we’re with you. Let’s level up — together.
      </p>
    </div>
    <div class="visual-section">
      <img
        src="https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?auto=format&fit=crop&w=600&q=80"
        alt="Focused athlete"
        class="main-image"
      />
    </div>
  </section>
</template>

<script>
export default {
  name: "AboutModern",
};
</script>

<style scoped>
.about-modern {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  padding: 4rem 3rem;
  width: 100%;
  max-width: 1400px;
  margin: 0 auto;
  background-color: #0f172a;
  color: #f1f5f9;
  border-radius: 20px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.5);
  animation: fadeIn 1.2s ease-in-out;
}

.text-section {
  flex: 1 1 600px;
  padding: 1rem 2rem;
  animation: slideInLeft 1.2s ease;
}

.title {
  font-size: 3.2rem;
  margin-bottom: 1.5rem;
  font-weight: 800;
  line-height: 1.2;
}

.gradient-text {
  background: linear-gradient(90deg, #34d399, #3b82f6);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.text-section p {
  font-size: 1.25rem;
  line-height: 1.8;
  margin-bottom: 1rem;
  color: #cbd5e1;
}

.visual-section {
  flex: 1 1 500px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  animation: slideInRight 1.2s ease;
}

.main-image {
  width: 100%;
  max-width: 450px;
  border-radius: 16px;
  box-shadow: 0 12px 25px rgba(0, 0, 0, 0.6);
  object-fit: cover;
}

/* Animations */
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes slideInLeft {
  from { opacity: 0; transform: translateX(-50px); }
  to { opacity: 1; transform: translateX(0); }
}

@keyframes slideInRight {
  from { opacity: 0; transform: translateX(50px); }
  to { opacity: 1; transform: translateX(0); }
}

/* Responsive tweaks */
@media (max-width: 1024px) {
  .about-modern {
    padding: 3rem 2rem;
  }
}

@media (max-width: 768px) {
  .about-modern {
    flex-direction: column-reverse;
    text-align: center;
    padding: 2rem 1rem;
  }

  .text-section,
  .visual-section {
    padding: 1rem 0;
  }

  .title {
    font-size: 2.2rem;
  }
}
</style>
