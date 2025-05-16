<template>
  <section class="about-page">
    <div class="content-wrapper">
      <h1>About Our Fitness Website</h1>
      <p>
        Welcome to <span class="highlight">FitLife</span>, your ultimate fitness companion.
        We believe fitness is more than exercise — it's a lifestyle that strengthens body, mind, and spirit.
      </p>
      <p>
        Our mission is to motivate and empower you through expert workout tips, balanced nutrition advice,
        and inspiring stories. Whether you're just starting out or pushing your limits, we’re here to guide you.
      </p>
      <p>
        Join thousands of users who’ve transformed their lives by embracing a healthier, happier lifestyle with FitLife.
        Let’s build your best self — together.
      </p>
    </div>
    <div class="image-wrapper">
      <img
        src="https://images.unsplash.com/photo-1594737625785-c1e30f2a298d?auto=format&fit=crop&w=600&q=80"
        alt="Fitness motivation"
      />
    </div>
  </section>
</template>

<script>
export default {
  name: "AboutPage",
};
</script>

<style scoped>
.about-page {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  padding: 3rem 1rem;
  background: linear-gradient(135deg, #6bc1ff, #1e3c72);
  color: white;
  border-radius: 12px;
  box-shadow: 0 10px 25px rgba(30, 60, 114, 0.4);
  max-width: 900px;
  margin: 2rem auto;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.content-wrapper {
  flex: 1 1 400px;
  padding: 1rem 2rem;
}

.content-wrapper h1 {
  font-size: 2.8rem;
  margin-bottom: 1.5rem;
  font-weight: 700;
  text-shadow: 2px 2px 6px rgba(0,0,0,0.3);
}

.content-wrapper p {
  font-size: 1.1rem;
  line-height: 1.7;
  margin-bottom: 1.25rem;
  text-shadow: 1px 1px 3px rgba(0,0,0,0.2);
}

.highlight {
  font-weight: 900;
  color: #ffdd57;
  text-shadow: 1px 1px 3px rgba(0,0,0,0.4);
}

.image-wrapper {
  flex: 1 1 300px;
  padding: 1rem 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

.image-wrapper img {
  max-width: 100%;
  border-radius: 15px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.5);
  object-fit: cover;
}
</style>
