<template>
  <div id="app">
    <HeaderComponent @navigate="currentPage = $event" />
    <main>
      <FitnessHome v-if="currentPage === 'home'" @navigate="currentPage = $event" />
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
      currentPage: 'home'
    }
  }
}
</script>
