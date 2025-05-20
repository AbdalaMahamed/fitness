<template>
  <section class="contact-container">
    <div class="language-toggle">
      <button :class="{ active: lang === 'nl' }" @click="lang = 'nl'">Nederlands</button>
      <button :class="{ active: lang === 'en' }" @click="lang = 'en'">English</button>
    </div>

    <h2>{{ texts.title }}</h2>
    <p>{{ texts.subtitle }}</p>

    <form class="contact-form" @submit.prevent="handleSubmit" v-if="!submitted">
      <input v-model="name" :placeholder="texts.namePlaceholder" required />
      <input v-model="email" type="email" :placeholder="texts.emailPlaceholder" required />
      <textarea v-model="message" :placeholder="texts.messagePlaceholder" rows="5" required></textarea>
      <button type="submit" :disabled="loading">
        {{ loading ? texts.sending : texts.sendButton }}
      </button>
    </form>

    <div v-if="submitted" class="success-message">
      <svg xmlns="http://www.w3.org/2000/svg" class="check-icon" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7" />
      </svg>
      <h3>{{ texts.thankYou }}, {{ name }}!</h3>
      <p>{{ texts.receivedMessage }}</p>
      <button @click="resetForm" class="reset-btn">{{ texts.sendAnother }}</button>
    </div>
  </section>
</template>

<script>
export default {
  name: "ContactPage",
  data() {
    return {
      lang: "nl", // default language
      name: "",
      email: "",
      message: "",
      submitted: false,
      loading: false,
      textsByLang: {
        nl: {
          title: "Neem Contact Op",
          subtitle: "Als je vragen hebt of wilt deelnemen, neem dan hieronder contact met ons op.",
          namePlaceholder: "Je Naam",
          emailPlaceholder: "Je E-mail",
          messagePlaceholder: "Je Bericht",
          sendButton: "Verzend Bericht",
          sending: "Bezig met verzenden...",
          thankYou: "Bedankt",
          receivedMessage: "We hebben je bericht ontvangen en nemen spoedig contact met je op.",
          sendAnother: "Verzend nog een bericht",
        },
        en: {
          title: "Contact Us",
          subtitle: "If you have any questions or want to join, reach out below.",
          namePlaceholder: "Your Name",
          emailPlaceholder: "Your Email",
          messagePlaceholder: "Your Message",
          sendButton: "Send Message",
          sending: "Sending...",
          thankYou: "Thank you",
          receivedMessage: "We have received your message and will contact you shortly.",
          sendAnother: "Send another message",
        },
      },
    };
  },
  computed: {
    texts() {
      return this.textsByLang[this.lang];
    },
  },
  methods: {
    async handleSubmit() {
      this.loading = true;

      // Simulate sending process (replace with real API call)
      await new Promise((r) => setTimeout(r, 1500));

      this.submitted = true;
      this.loading = false;
    },
    resetForm() {
      this.name = "";
      this.email = "";
      this.message = "";
      this.submitted = false;
    },
  },
};
</script>

<style scoped>
.contact-container {
  padding: 2rem;
  max-width: 700px;
  margin: 0 auto;
  text-align: center;
  font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
  color: #111;
}

/* Language toggle */
.language-toggle {
  margin-bottom: 1.5rem;
}
.language-toggle button {
  background: none;
  border: 2px solid #000;
  padding: 0.5rem 1rem;
  margin: 0 0.25rem;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 600;
  transition: background-color 0.3s, color 0.3s;
}
.language-toggle button.active,
.language-toggle button:hover {
  background-color: #000;
  color: white;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.contact-form input,
.contact-form textarea {
  padding: 0.75rem;
  border: 1px solid #ccc;
  border-radius: 8px;
  font-size: 1rem;
  transition: border-color 0.3s;
}
.contact-form input:focus,
.contact-form textarea:focus {
  border-color: #000;
  outline: none;
}

.contact-form button {
  padding: 0.75rem;
  background-color: #000;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-weight: bold;
  transition: background-color 0.3s ease;
}

.contact-form button:disabled {
  background-color: #555;
  cursor: not-allowed;
}

.contact-form button:hover:not(:disabled) {
  background-color: #d10505;
}

/* Success message styling */
.success-message {
  background: #e6f4ea;
  border: 2px solid #27ae60;
  border-radius: 12px;
  padding: 2rem;
  color: #2c6a2c;
  animation: fadeIn 0.7s ease forwards;
  display: inline-block;
  max-width: 500px;
  margin: 0 auto;
}

.check-icon {
  width: 60px;
  height: 60px;
  stroke: #27ae60;
  margin-bottom: 1rem;
}

.reset-btn {
  margin-top: 1.5rem;
  background: transparent;
  border: 2px solid #27ae60;
  color: #27ae60;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 600;
  transition: background-color 0.3s, color 0.3s;
}

.reset-btn:hover {
  background-color: #27ae60;
  color: white;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
