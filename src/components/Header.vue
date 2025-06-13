<template>
  <header class="header">
    <div class="logo">
      <img src="@/assets/logo1.png" alt="Logo" />
      <span></span>
    </div>

    <button class="hamburger" @click="toggleMenu" aria-label="Toggle navigation">
      <span :class="{ open: menuOpen }"></span>
      <span :class="{ open: menuOpen }"></span>
      <span :class="{ open: menuOpen }"></span>
    </button>

    <nav :class="['nav', { open: menuOpen }]">
      <button @click="$emit('navigate', 'home')">Home</button>
      <button @click="$emit('navigate', 'fitness')">Workouts</button>
      <button @click="$emit('navigate', 'nutrition')">Nutrition Plan</button>
      <button @click="$emit('navigate', 'contact')">Contact</button>
      <button @click="$emit('navigate', 'about')">About Us</button>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'HeaderComponent',
  data() {
    return {
      menuOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen;
    }
  }
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  background-color: #000;
  color: #fff;
  position: sticky;
  top: 0;
  z-index: 1000;
  box-shadow: 0 4px 12px rgba(255, 255, 255, 0.05);
}

.logo {
  display: flex;
  align-items: center;
  gap: 0.8rem;
}

.logo img {
  height: 60px; /* iets kleiner voor mobiel en desktop */
  object-fit: contain;
}

.logo span {
  font-size: 1.5rem;
  font-weight: 700;
  letter-spacing: 1px;
  color: #fff;
}

/* Nav standaard desktop */
.nav {
  display: flex;
  gap: 1rem;
}

.nav button {
  background: transparent;
  color: #fff;
  border: none;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  padding: 0.6rem 1rem;
  position: relative;
  transition: color 0.3s ease;
}

.nav button::after {
  content: "";
  position: absolute;
  bottom: 6px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 2px;
  background-color: #fff;
  transition: width 0.3s ease;
}

.nav button:hover {
  color: #facc15;
}

.nav button:hover::after {
  width: 100%;
  background-color: #facc15;
}

/* Hamburger knop */
.hamburger {
  display: none;
  flex-direction: column;
  justify-content: space-between;
  width: 25px;
  height: 20px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
}

.hamburger span {
  display: block;
  height: 3px;
  background: white;
  border-radius: 2px;
  transition: all 0.3s ease;
  transform-origin: 1px;
}

.hamburger span.open:nth-child(1) {
  transform: rotate(45deg);
}

.hamburger span.open:nth-child(2) {
  opacity: 0;
}

.hamburger span.open:nth-child(3) {
  transform: rotate(-45deg);
}

/* Mobiel: hamburger tonen, menu verbergen */
@media (max-width: 768px) {
  .hamburger {
    display: flex;
  }

  .nav {
    display: none;
    flex-direction: column;
    width: 100%;
    margin-top: 0.5rem;
  }

  .nav.open {
    display: flex;
  }

  .nav button {
    flex: 1 1 100%;
    text-align: left;
    padding: 0.75rem 0;
    border-top: 1px solid #333;
  }
}
</style>
