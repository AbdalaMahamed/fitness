<template>
  <header class="header">
    <div class="logo">
      <h1>💪 FitnessPro</h1>
    </div>
    <nav class="nav">
      <button @click="$emit('navigate', 'home')">Home</button>
      <button @click="$emit('navigate', 'fitness')">Fitness</button>
      <button @click="$emit('navigate', 'contact')">Contact</button>
      <button @click="$emit('navigate', 'about')">About Us</button>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'HeaderComponent'
}
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  background: linear-gradient(90deg, #111 0%, #222 100%);
  box-shadow: 0 4px 15px rgba(0,0,0,0.5);
  position: sticky;
  top: 0;
  z-index: 1000;
}

.logo h1 {
  font-size: 1.8rem;
  color: #ffdd57;
  margin: 0;
  font-weight: 800;
  letter-spacing: 1px;
}

.nav button {
  margin: 0 0.8rem;
  color: #fff;
  background: transparent;
  border: 2px solid transparent;
  padding: 0.5rem 1rem;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
  border-radius: 30px;
}

.nav button:hover {
  border-color: #ffdd57;
  color: #ffdd57;
  background-color: rgba(255, 221, 87, 0.1);
  box-shadow: 0 0 10px rgba(255, 221, 87, 0.3);
}

@media (max-width: 768px) {
  .header {
    flex-direction: column;
    padding: 1rem;
  }

  .nav {
    margin-top: 1rem;
  }

  .nav button {
    margin: 0.5rem 0.5rem;
    width: 120px;
  }
}
</style>
