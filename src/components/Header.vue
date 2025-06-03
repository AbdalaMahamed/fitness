<template>
  <header class="header">
    <div class="logo">
      <img src="@/assets/logo1.png" alt="Logo" />
      <span></span>
    </div>

    <nav class="nav">
      <button @click="$emit('navigate', 'home')">Home</button>
      <button @click="$emit('navigate', 'fitness')">Workouts</button>
      <!-- Fixed button closing tag -->
<button @click="$emit('navigate', 'nutrition')">Nutrition Plan</button>
      <button @click="$emit('navigate', 'contact')">Contact</button>
      <button @click="$emit('navigate', 'about')">About Us</button>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'HeaderComponent',
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
  border-bottom: 1px solid #333;
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
  height: 100px;
  object-fit: contain;
}

.logo span {
  font-size: 1.5rem;
  font-weight: 700;
  letter-spacing: 1px;
  color: #fff;
}

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

@media (max-width: 768px) {
  .header {
    flex-direction: column;
    align-items: flex-start;
  }

  .nav {
    flex-wrap: wrap;
    width: 100%;
    margin-top: 0.5rem;
  }

  .nav button {
    flex: 1 1 100%;
    text-align: left;
    padding: 0.75rem 0;
    border-top: 1px solid #333;
  }
}
</style>
