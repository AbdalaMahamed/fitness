<template>
  <footer class="footer">
    <link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"
/>

    <div class="footer-content">
      <div class="brand">
       
        <p>&copy; 2025 WolfRep. All rights reserved.</p>
      </div>

      <div class="social-links">
        <a href="https://facebook.com" target="_blank" aria-label="Facebook">
          <i class="fab fa-facebook-f"></i>
        </a>
        <a href="https://twitter.com" target="_blank" aria-label="Twitter">
          <i class="fab fa-twitter"></i>
        </a>
        <a href="https://instagram.com" target="_blank" aria-label="Instagram">
          <i class="fab fa-instagram"></i>
        </a>
        <a href="https://youtube.com" target="_blank" aria-label="YouTube">
          <i class="fab fa-youtube"></i>
        </a>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'FooterComponent',
};
</script>

<style scoped>
.footer {
  background-color: #000;
  color: #fff;
  padding: 2rem 1rem;
  text-align: center;
  border-top: 1px solid #222;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
  align-items: center;
}

.brand h2 {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 0.4rem;
  color: #fff;
}

.brand p {
  font-size: 0.9rem;
  color: #ccc;
}

.social-links {
  display: flex;
  gap: 1.2rem;
  justify-content: center;
}

.social-links a {
  color: #fff;
  font-size: 1.25rem;
  transition: color 0.3s ease;
}

.social-links a:hover {
  color: #facc15;
}
</style>
