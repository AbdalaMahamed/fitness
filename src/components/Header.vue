<template>
  <header class="header">
    <div class="logo">
      <img src="@/assets/WORK-Logo_W 1.png" alt="Logo" />
    </div>
    <nav class="nav">
      <button @click="$emit('navigate', 'home')">Home</button>
      <button @click="$emit('navigate', 'fitness')">Workouts</button>
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
  background: linear-gradient(90deg, #0f2027, #203a43, #2c5364);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
  position: sticky;
  top: 0;
  z-index: 1000;
}

.logo img {
  max-height: 60px;
  width: auto;
  object-fit: contain;
}

.nav {
  display: flex;
  align-items: center;
}

.nav button {
  margin: 0 0.75rem;
  background: none;
  border: 2px solid transparent;
  color: #fff;
  font-size: 1rem;
  padding: 0.5rem 1.2rem;
  border-radius: 50px;
  cursor: pointer;
  font-weight: 600;
  transition: 0.3s ease all;
  position: relative;
}

.nav button::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 50%;
  width: 0%;
  height: 2px;
  background-color: #ffd700;
  transition: width 0.3s ease, left 0.3s ease;
}

.nav button:hover::after {
  width: 100%;
  left: 0;
}

.nav button:hover {
  color: #ffd700;
}

@media (max-width: 768px) {
  .header {
    flex-direction: column;
    padding: 1rem;
  }

  .logo {
    margin-bottom: 1rem;
  }

  .nav {
    flex-wrap: wrap;
    justify-content: center;
  }

  .nav button {
    margin: 0.5rem;
  }
}
</style>
