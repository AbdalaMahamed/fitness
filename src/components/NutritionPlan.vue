<template>
  <div class="product-page">

    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-content">
        <div class="text-block">
          <h1>The Ultimate Guide to Body Recomposition</h1>
          <p>Learn to build muscle and lose fat simultaneously with science-based training and nutrition strategies.</p>
          <button @click="buyProduct" class="buy-btn">Buy Now - $49</button>
          <p class="guarantee">30-day money-back guarantee</p>
        </div>
        <div class="image-block">
          <img src="https://i.pinimg.com/736x/3e/a4/55/3ea455608afb98246896c214dcb65a8c.jpg" alt="Ultimate Guide to Body Recomposition" />
        </div>
      </div>
    </section>

    <!-- Features Section -->
    <section class="features">
      <h2>What You'll Get</h2>
      <ul>
        <li><strong>Comprehensive Training Plans:</strong> Structured workouts designed for fat loss and muscle gain.</li>
        <li><strong>Nutrition Guide:</strong> Macro tracking and meal plans optimized for recomposition.</li>
        <li><strong>Video Tutorials:</strong> Step-by-step exercise demonstrations and coaching tips.</li>
        <li><strong>Progress Tracking:</strong> Tools and templates to monitor your progress effectively.</li>
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
  name: "BodyRecompositionGuide",
  data() {
    return {
      testimonials: [
        { name: "Alex P.", quote: "This guide transformed the way I train and eat. Lost fat and gained muscle like never before!" },
        { name: "Samantha L.", quote: "Clear, actionable, and backed by science. Worth every penny." },
        { name: "Michael W.", quote: "The best body recomposition resource I've found. Highly recommend." },
      ],
      faqs: [
        {
          question: "Is this guide suitable for beginners?",
          answer: "Yes, it covers foundational principles and also advanced techniques for all levels.",
          open: false,
        },
        {
          question: "Do I need a gym membership?",
          answer: "Most training plans require gym equipment, but there are alternative home workouts included.",
          open: false,
        },
        {
          question: "How long until I see results?",
          answer: "Results vary but many users notice changes within 8-12 weeks following the program.",
          open: false,
        },
      ],
    };
  },
  methods: {
    buyProduct() {
      // Redirect to checkout or purchase link
      window.open('https://jeffnippard.com/checkout-url', '_blank');
    },
    toggleFaq(item) {
      item.open = !item.open;
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
