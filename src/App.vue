<template>
  <div id="app">
    <HeaderComponent @navigate="navigateTo" />
    <main>
      <FitnessHome v-if="currentPage === 'home'" @navigate="navigateTo" />
      <FitnessPage v-else-if="currentPage === 'fitness'" />
      <NutritionPlan v-else-if="currentPage === 'nutrition'" />
      <AboutPage v-else-if="currentPage === 'about'" />
      <ContactPage v-else-if="currentPage === 'contact'" />
    </main>
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
import NutritionPlan from './components/NutritionPlan.vue'

export default {
  name: 'App',
  components: { HeaderComponent, FooterComponent, FitnessHome, FitnessPage, NutritionPlan, AboutPage, ContactPage },
  data() {
    return {
      currentPage: localStorage.getItem('currentPage') || 'home',
    }
  },
  methods: {
    navigateTo(page) {
      this.currentPage = page;
      localStorage.setItem('currentPage', page);
      history.pushState({ page }, '', page === 'home' ? '/' : `/${page}`);
    },
    onPopState(event) {
      if (event.state && event.state.page) {
        this.currentPage = event.state.page;
        localStorage.setItem('currentPage', event.state.page);
      } else {
        this.currentPage = 'home';
        localStorage.setItem('currentPage', 'home');
      }
    }
  },
  created() {
    // Initialize URL and state on load
    const path = window.location.pathname.replace('/', '') || 'home';
    this.currentPage = path;
    localStorage.setItem('currentPage', path);

    window.addEventListener('popstate', this.onPopState);

    // Also push initial state if no history state exists yet
    if (!history.state) {
      history.replaceState({ page: this.currentPage }, '', window.location.pathname);
    }
  },
  beforeUnmount() {
    window.removeEventListener('popstate', this.onPopState);
  }
}
</script>
