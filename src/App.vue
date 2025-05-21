<template>
  <div id="app">
    <HeaderComponent @navigate="currentPage = $event" />

    <div class="page-content">
      <FitnessHome v-if="currentPage === 'home'" />
      <FitnessPage v-else-if="currentPage === 'fitness'" />
      <AboutPage v-else-if="currentPage === 'about'" />
      <ContactPage v-else-if="currentPage === 'contact'" />
    </div>

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
