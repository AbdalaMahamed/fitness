<template>
  <div id="app">
    <HeaderComponent @navigate="currentPage = $event" />

    <div class="page-content">
      <div v-if="currentPage === 'home'">
        <HelloWorld msg="Welcome to Your Vue.js App" />
      </div>

      <div v-if="currentPage === 'fitness'">
        <FitnessPage />
      </div>

      <div v-if="currentPage === 'contact'">
        <h1>Contact Page</h1>
        <p>Contact us for more information.</p>
      </div>

      <div v-if="currentPage === 'about'">
        <AboutPage />
      </div>
    </div>

    <FooterComponent />
  </div>
</template>

<script>
import HeaderComponent from './components/Header.vue'
import FooterComponent from './components/Footer.vue'
import HelloWorld from './components/HelloWorld.vue'
import AboutPage from './components/About.vue'
import FitnessPage from './components/Fitness.vue'  // Let op hier

export default {
  name: 'App',
  components: {
    HeaderComponent,
    FooterComponent,
    HelloWorld,
    AboutPage,
    FitnessPage,
  },
  data() {
    return {
      currentPage: 'home'
    }
  }
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.page-content {
  flex: 1;
  padding: 1rem 2rem;
  max-width: 900px;
  margin: 0 auto;
  box-sizing: border-box;
}
</style>
