<template>
  <div id="app">
    <!-- Header -->
    <HeaderComponent @navigate="currentPage = $event" />

    <!-- Main content area -->
    <div class="page-content">
      <FitnessHome v-if="currentPage === 'home'" @navigate="currentPage = $event" />
      <FitnessPage v-else-if="currentPage === 'fitness'" />
      <AboutPage v-else-if="currentPage === 'about'" />
      <ContactPage v-else-if="currentPage === 'contact'" />
    </div>

    <!-- Footer -->
    <FooterComponent />
  </div>
</template>

<script>
import HeaderComponent from './components/Header.vue'
import FooterComponent from './components/Footer.vue'
import FitnessHome from './components/FitnessHome.vue'
import FitnessPage from './components/Fitness.vue'
import AboutPage from './components/About.vue'
import ContactPage from './components/ContactPage.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    FooterComponent,
    FitnessHome,
    FitnessPage,
    AboutPage,
    ContactPage,
  },
  data() {
    return {
      currentPage: 'home',
    }
  },
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background-color: #f8fafc;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #1e293b;
  margin: 0;
}

.page-content {
  flex: 1;
  padding: 2rem 1rem;
}
</style>
