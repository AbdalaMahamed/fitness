<template>
  <div id="app">
    <HeaderComponent @navigate="currentPage = $event" />

    <div class="page-content">
      <HelloWorld v-if="currentPage === 'home'" msg="Welcome to Your Vue.js App" />
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
import HelloWorld from './components/HelloWorld.vue'
import AboutPage from './components/About.vue'
import FitnessPage from './components/Fitness.vue'
import ContactPage from './components/ContactPage.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    FooterComponent,
    HelloWorld,
    AboutPage,
    FitnessPage,
    ContactPage
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
