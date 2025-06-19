<template>
  <header class="header">
    <div class="logo">
      <img src="@/assets/logo1.png" alt="Logo" />
      <span></span>
    </div>

    <button class="hamburger" :class="{ open: menuOpen }" @click="toggleMenu" aria-label="Toggle navigation">
      <span></span>
      <span></span>
      <span></span>
    </button>

    <nav :class="['nav', { open: menuOpen }]">
      <button @click="navigateAndCloseMenu('home')">Home</button>
      <button @click="navigateAndCloseMenu('fitness')">Workouts</button>
      <button @click="navigateAndCloseMenu('nutrition')">Nutrition Plan</button>
      <button @click="navigateAndCloseMenu('contact')">Contact</button>
      <button @click="navigateAndCloseMenu('about')">About Us</button>
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
    },
    navigateAndCloseMenu(page) {
      this.$emit('navigate', page);
      this.menuOpen = false;
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
  height: 60px;
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
  position: relative;
  z-index: 1100;
}

.hamburger span {
  display: block;
  height: 3px;
  background: white;
  border-radius: 2px;
  transition: all 0.3s ease;
}

/* Geen kruis-animatie bij openen */
.hamburger.open span:nth-child(1),
.hamburger.open span:nth-child(2),
.hamburger.open span:nth-child(3) {
  transform: none;
  opacity: 1;
}

/* Mobiel */
@media (max-width: 768px) {
  .hamburger {
    display: flex;
    position: absolute;
    top: 1.4rem;
    right: 2rem;
  }

  .nav {
    display: none;
    flex-direction: column;
    width: 100%;
    margin-top: 0.5rem;
    background-color: #000;
    position: absolute;
    top: 100%;
    left: 0;
  }

  .nav.open {
    display: flex;
  }

  .nav button {
    flex: 1 1 100%;
    text-align: left;
    border-top: 1px solid #333;
  }
}
</style>
