<template>
  <div class="product-page">

    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-content">
        <div class="text-block">
          <h1>The Complete Nutrition Guide for Building Muscle and Losing Fat</h1>
          <p>Discover how smart nutrition helps you gain muscle and lose fat at the same time.</p>
          <button @click="buyProduct" class="buy-btn">Buy Now - $49</button>
          <p class="guarantee">30-day money-back guarantee</p>
        </div>
        <div class="image-block">
          <img
            src="https://i.pinimg.com/736x/3e/a4/55/3ea455608afb98246896c214dcb65a8c.jpg"
            alt="Nutrition Guide for Muscle Building and Fat Loss"
            loading="lazy"
          />
        </div>
      </div>
    </section>

    <!-- Features Section -->
    <section class="features">
      <h2>What You'll Get</h2>
      <ul>
        <li><strong>Detailed Nutrition Plans:</strong> Simple, effective meal plans for muscle growth and fat loss.</li>
        <li><strong>Macros and Calories:</strong> Learn how to track macros to reach your goals.</li>
        <li><strong>Video Tutorials:</strong> Step-by-step nutrition advice and practical tips.</li>
        <li><strong>Progress Tracking:</strong> Easy-to-use tools to monitor your results.</li>
      </ul>
    </section>

    <!-- Testimonials Section -->
    <section class="testimonials">
      <h2>What Our Clients Say</h2>
      <div class="testimonial-list">
        <div class="testimonial" v-for="testimonial in testimonials" :key="testimonial.name">
          <p>“{{ testimonial.quote }}”</p>
          <h4>- {{ testimonial.name }}</h4>
        </div>
      </div>
    </section>

    <!-- FAQ Section -->
    <section class="faq">
      <h2>Frequently Asked Questions</h2>
      <div v-for="item in faqs" :key="item.question" class="faq-item">
        <h3 @click="toggleFaq(item)" class="question">
          {{ item.question }}
          <span>{{ item.open ? '-' : '+' }}</span>
        </h3>
        <p v-if="item.open" class="answer">{{ item.answer }}</p>
      </div>
    </section>

  </div>
</template>

<script>
export default {
  name: "NutritionGuide",
  data() {
    return {
      testimonials: [
        { name: "Alex P.", quote: "This guide helped me understand my nutrition better and I see real results." },
        { name: "Samantha L.", quote: "Clear and easy-to-follow nutrition advice that really works." },
        { name: "Michael W.", quote: "Perfect balance between muscle building and fat loss. Highly recommended!" },
      ],
      faqs: [
        {
          question: "Is this guide suitable for beginners?",
          answer: "Yes, it explains everything step-by-step and is great for all levels.",
          open: false,
        },
        {
          question: "Can I follow this without special supplements?",
          answer: "Absolutely, the focus is on food and training; supplements are optional.",
          open: false,
        },
        {
          question: "How soon will I see results?",
          answer: "With consistency, most people notice changes within 8-12 weeks.",
          open: false,
        },
      ],
    };
  },
  methods: {
    buyProduct() {
      window.location.href = 'https://payhip.com/b/YourProductCode'; // Pas aan naar jouw checkout URL
    },
    toggleFaq(item) {
      item.open = !item.open;
    }
  },
  metaInfo() {
    return {
      title: 'Nutrition Guide for Muscle Building and Fat Loss | YourSiteName',
      meta: [
        {
          name: 'description',
          content: 'Learn how to build muscle and lose fat with smart nutrition. Includes meal plans, macro tracking, and helpful tools.'
        }
      ]
    }
  }
};
</script>

<style scoped>
.product-page {
  font-family: 'Poppins', sans-serif;
  color: #1e293b;
  max-width: 1000px;
  margin: 0 auto;
  padding: 2rem 1rem;
}

/* Hero Section */
.hero {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 3rem;
}
.hero-content {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  max-width: 900px;
  width: 100%;
  align-items: center;
}
.text-block {
  flex: 1 1 400px;
}
.text-block h1 {
  font-size: 2.8rem;
  margin-bottom: 1rem;
  font-weight: 700;
}
.text-block p {
  font-size: 1.2rem;
  margin-bottom: 1.5rem;
}
.buy-btn {
  background-color: #e11d48;
  border: none;
  color: white;
  padding: 1rem 2.5rem;
  font-size: 1.2rem;
  border-radius: 9999px;
  cursor: pointer;
  font-weight: 700;
  transition: background-color 0.3s ease;
}
.buy-btn:hover {
  background-color: #be123c;
}
.guarantee {
  margin-top: 0.5rem;
  font-size: 0.9rem;
  color: #64748b;
}
.image-block {
  flex: 1 1 400px;
  text-align: center;
}
.image-block img {
  max-width: 100%;
  border-radius: 12px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.15);
}

/* Features Section */
.features {
  margin-bottom: 3rem;
}
.features h2 {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 1rem;
  text-align: center;
}
.features ul {
  list-style: none;
  padding: 0;
  max-width: 700px;
  margin: 0 auto;
}
.features li {
  background: #f9fafb;
  padding: 1rem 1.5rem;
  margin-bottom: 1rem;
  border-radius: 8px;
  font-size: 1.1rem;
  color: #334155;
  box-shadow: 0 2px 10px rgba(0,0,0,0.05);
}

/* Testimonials Section */
.testimonials {
  margin-bottom: 3rem;
  text-align: center;
}
.testimonials h2 {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 2rem;
}
.testimonial-list {
  display: flex;
  gap: 2rem;
  flex-wrap: wrap;
  justify-content: center;
}
.testimonial {
  max-width: 320px;
  background: white;
  padding: 1.5rem 2rem;
  border-radius: 12px;
  box-shadow: 0 6px 15px rgba(0,0,0,0.08);
  font-style: italic;
  color: #475569;
  transition: box-shadow 0.3s ease;
}
.testimonial:hover {
  box-shadow: 0 15px 30px rgba(0,0,0,0.15);
}
.testimonial p {
  margin-bottom: 1rem;
  font-size: 1.1rem;
}
.testimonial h4 {
  font-weight: 700;
  color: #0f172a;
  margin: 0;
  text-align: right;
}

/* FAQ Section */
.faq {
  max-width: 700px;
  margin: 0 auto 4rem;
}
.faq h2 {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 1rem;
  text-align: center;
}
.faq-item {
  background: #f9fafb;
  margin-bottom: 1rem;
  border-radius: 8px;
  padding: 1rem 1.5rem;
  box-shadow: 0 2px 10px rgba(0,0,0,0.05);
}
.question {
  font-weight: 700;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 1.1rem;
}
.answer {
  margin-top: 0.5rem;
  font-size: 1rem;
  color: #475569;
}

/* Responsive */
@media (max-width: 768px) {
  .hero-content {
    flex-direction: column;
  }
  .text-block, .image-block {
    flex: 1 1 100%;
  }
  .testimonial-list {
    flex-direction: column;
    align-items: center;
  }
}
</style>
