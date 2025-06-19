<template>
  <main class="contact-container">
    <!-- Banner Image -->
    <img
      class="banner-image"
      src="https://www.verywellfit.com/thmb/dT2j--w4-qV_dXTGu7NsnQCYC0A=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc()/1229823-GettyImages-1370779225-1c0cadcb4dd045daa2dad4e3040acf65.jpg"
      alt="Contact Banner"
    />

    <h1>Contact</h1>

    <section class="contact-info">
      <h2>Question About Your Order?</h2>
      <p>
        Send an email to
        <a href="mailto:info@wolfrep.com">info@wolfrep.com</a> and please allow
        3-5 business days for a reply.
      </p>

      <h2>Money Back Information</h2>
      <p>
        We review your request and respond via email, and if approved, a credit will be
        issued within 30 days. Contact the card-issuing bank for details.
      </p>

      <h2>Still Need Help?</h2>
      <p>
        If you have any feedback or questions about our website or our service in general,
        please send us a message by completing our enquiry form below.
      </p>
    </section>

    <section class="form-section">
      <div class="form-image-wrapper">
        <img
          src="https://jeffnippard.com/cdn/shop/files/contact-jeff-nippard.png?v=1713843553&width=800"
          alt="Contact Illustration"
          class="form-image"
        />
      </div>

      <form @submit.prevent="submitForm" novalidate>
        <h2>Enquiry Form</h2>

        <label>
          Full Name *
          <input
            type="text"
            v-model.trim="form.fullName"
            required
            placeholder="Your full name"
          />
        </label>

        <label>
          Email *
          <input
            type="email"
            v-model.trim="form.email"
            required
            placeholder="Your email address"
          />
        </label>

        <label>
          Subject *
          <input
            type="text"
            v-model.trim="form.subject"
            required
            placeholder="Subject of your enquiry"
          />
        </label>

        <label>
          Order Number
          <input
            type="text"
            v-model.trim="form.orderNumber"
            placeholder="If applicable"
          />
        </label>

        <label>
          Message *
          <textarea
            v-model.trim="form.message"
            required
            placeholder="Your message"
            rows="6"
          ></textarea>
        </label>

        <button type="submit" :disabled="loading">
          {{ loading ? 'Submitting...' : 'Submit' }}
        </button>

        <p v-if="successMessage" class="success-message">{{ successMessage }}</p>
        <p v-if="errorMessage" class="error-message">{{ errorMessage }}</p>
      </form>
    </section>
  </main>
</template>

<script>
export default {
  name: 'ContactPage',
  data() {
    return {
      form: {
        fullName: '',
        email: '',
        subject: '',
        orderNumber: '',
        message: '',
      },
      loading: false,
      successMessage: '',
      errorMessage: '',
    };
  },
  methods: {
    async submitForm() {
      this.successMessage = '';
      this.errorMessage = '';
      this.loading = true;

      if (
        !this.form.fullName ||
        !this.form.email ||
        !this.form.subject ||
        !this.form.message
      ) {
        this.errorMessage = 'Please fill out all required fields.';
        this.loading = false;
        return;
      }

      try {
        // Simulate API call delay
        await new Promise((resolve) => setTimeout(resolve, 1500));

        // Reset form on success
        this.successMessage =
          'Thank you for your message! We will get back to you shortly.';
        this.form = {
          fullName: '',
          email: '',
          subject: '',
          orderNumber: '',
          message: '',
        };
      } catch {
        this.errorMessage = 'Oops! Something went wrong. Please try again later.';
      } finally {
        this.loading = false;
      }
    },
  },
};
</script>

<style scoped>
.contact-container {
  max-width: 900px;
  margin: 3rem auto 5rem;
  font-family: 'Helvetica Neue', Arial, sans-serif;
  color: #222;
  padding: 0 1rem;
}

.banner-image {
  width: 50%;
  height: 100%;
  border-radius: 8px;
  margin-bottom: 2.5rem;
  object-fit: cover;
}

h1 {
  font-weight: 700;
  font-size: 2.8rem;
  margin-bottom: 2rem;
  text-align: center;
  color: #d32f2f;
}

.contact-info {
  margin-bottom: 3rem;
  line-height: 1.6;
  font-size: 1.1rem;
  color: #444;
}

.contact-info h2 {
  font-weight: 600;
  margin-top: 2rem;
  margin-bottom: 0.5rem;
  color: #d32f2f;
}

.contact-info a {
  color: #d32f2f;
  text-decoration: underline;
}

.form-section {
  display: flex;
  gap: 3rem;
  align-items: flex-start;
  flex-wrap: wrap;
}

.form-image-wrapper {
  flex: 1 1 300px;
  max-width: 350px;
}

.form-image {
  width: 100%;
  border-radius: 8px;
  object-fit: cover;
}

form {
  flex: 1 1 400px;
  display: flex;
  flex-direction: column;
}

form h2 {
  font-weight: 600;
  margin-bottom: 1.5rem;
  color: #d32f2f;
  text-align: left;
}

label {
  display: flex;
  flex-direction: column;
  font-weight: 500;
  color: #555;
  font-size: 1rem;
  margin-bottom: 1rem;
}

input,
textarea {
  margin-top: 0.5rem;
  padding: 0.6rem 0.8rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-family: inherit;
  resize: vertical;
  transition: border-color 0.2s ease;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #d32f2f;
  box-shadow: 0 0 3px #d32f2f;
}

button {
  margin-top: 1rem;
  background-color: #d32f2f;
  color: white;
  border: none;
  padding: 0.85rem 2rem;
  border-radius: 4px;
  font-weight: 600;
  font-size: 1.1rem;
  cursor: pointer;
  transition: background-color 0.3s ease;
  align-self: flex-start;
  width: 150px;
}

button:disabled {
  background-color: #f29999;
  cursor: not-allowed;
}

button:hover:not(:disabled) {
  background-color: #a52828;
}

.success-message {
  margin-top: 1rem;
  color: #388e3c;
  font-weight: 600;
  text-align: left;
}

.error-message {
  margin-top: 1rem;
  color: #d32f2f;
  font-weight: 600;
  text-align: left;
}

/* Responsive */
@media (max-width: 1024px) {
  .banner-image {
    width: 75%;
  }
}

@media (max-width: 768px) {
  .form-section {
    flex-direction: column;
  }

  .form-image-wrapper,
  form {
    max-width: 100%;
    flex: none;
  }

  .banner-image {
    width: 90%;
  }

  button {
    width: 100%;
    max-width: 300px;
  }
}

@media (max-width: 480px) {
  h1 {
    font-size: 2rem;
  }

  .contact-info {
    font-size: 1rem;
  }

  button {
    font-size: 1rem;
    padding: 0.75rem;
  }
}

</style>
