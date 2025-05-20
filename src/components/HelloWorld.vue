<template>
  <main>
    <!-- Language Switch -->
    <div class="language-switch">
      <button 
        :class="{ active: language === 'en' }" 
        @click="language = 'en'"
        aria-label="Switch to English"
      >
        EN
      </button>
      <button 
        :class="{ active: language === 'nl' }" 
        @click="language = 'nl'"
        aria-label="Switch to Dutch"
      >
        NL
      </button>
    </div>

    <!-- Hero Section -->
    <section class="hero">
      <div class="overlay">
        <div class="hero-content">
          <h1>{{ texts.hero.title }}</h1>
          <p>{{ texts.hero.subtitle }}</p>
          <button @click="$emit('navigate', 'fitness')">
            {{ texts.hero.cta }}
          </button>
        </div>
      </div>
    </section>

    <!-- Features Section -->
    <section class="features">
      <div class="feature" v-for="feature in texts.features" :key="feature.title">
        <div class="icon">{{ feature.icon }}</div>
        <h3>{{ feature.title }}</h3>
        <p>{{ feature.description }}</p>
      </div>
    </section>

    <!-- About Section -->
    <section class="about">
      <h2>{{ texts.about.title }}</h2>
      <p>{{ texts.about.description }}</p>
    </section>
  </main>
</template>

<script>
export default {
  name: "HomePage",
  data() {
    return {
      language: 'en',
      content: {
        en: {
          hero: {
            title: "Train Slim, Train Strong",
            subtitle: "Join us to get personalized workouts and reach your fitness goals.",
            cta: "Start Workout"
          },
          features: [
            {
              icon: "🏋️‍♂️",
              title: "Expert Coaching",
              description: "Train with guidance from top fitness coaches tailored to you."
            },
            {
              icon: "📅",
              title: "Flexible Schedule",
              description: "Workout anytime, anywhere with our flexible plans."
            },
            {
              icon: "📈",
              title: "Track Progress",
              description: "Stay motivated by tracking your fitness improvements."
            }
          ],
          about: {
            title: "Why Choose Us?",
            description: "We believe fitness is for everyone. Our approach is simple: effective workouts, expert support, and a community that motivates you to be your best."
          }
        },
        nl: {
          hero: {
            title: "Train Slim, Train Sterk",
            subtitle: "Doe mee en ontvang gepersonaliseerde workouts om je fitnessdoelen te bereiken.",
            cta: "Begin met trainen" 
            //this.$router.push('/Fitness')

          },
          features: [
            {
              icon: "🏋️‍♂️",
              title: "Deskundige Coaching",
              description: "Train met begeleiding van top fitnesscoaches, afgestemd op jou."
            },
            {
              icon: "📅",
              title: "Flexibel Schema",
              description: "Train wanneer en waar je wilt met onze flexibele plannen."
            },
            {
              icon: "📈",
              title: "Volg Vooruitgang",
              description: "Blijf gemotiveerd door je fitnessverbeteringen bij te houden."
            }
          ],
          about: {
            title: "Waarom voor ons kiezen?",
            description: "Wij geloven dat fitness voor iedereen is. Onze aanpak is simpel: effectieve workouts, deskundige ondersteuning en een community die je motiveert om het beste uit jezelf te halen."
          }
        }
      }
    };
  },
  computed: {
    texts() {
      return this.content[this.language];
    }
  }
};
</script>

<style scoped>
/* Language Switcher */
.language-switch {
  display: flex;
  justify-content: flex-end;
  padding: 1rem 2rem;
  gap: 1rem;
}

.language-switch button {
  background: transparent;
  border: 2px solid #d10505;
  color: #d10505;
  font-weight: bold;
  padding: 0.4rem 1rem;
  border-radius: 5px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.language-switch button.active,
.language-switch button:hover {
  background-color: #d10505;
  color: white;
}

/* Reset some basics */
main {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #111;
}

/* Hero Section */
.hero {
  position: relative;
  height: 100vh;
  background: url('https://static.wixstatic.com/media/80cc9e_e02aeea7e20141bf8ba8ce03b1672e93~mv2.jpg/v1/fill/w_1901,h_940,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/80cc9e_e02aeea7e20141bf8ba8ce03b1672e93~mv2.jpg') center/cover no-repeat;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: white;
}

.hero .overlay {
  position: absolute;
  inset: 0;
  background: rgba(0,0,0,0.6);
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2rem;
}

.hero-content {
  max-width: 700px;
  z-index: 2;
}

.hero-content h1 {
  font-size: 4rem;
  font-weight: 900;
  margin-bottom: 1rem;
  text-shadow: 2px 2px 10px rgba(0,0,0,0.8);
}

.hero-content p {
  font-size: 1.5rem;
  margin-bottom: 2rem;
  text-shadow: 1px 1px 8px rgba(0,0,0,0.8);
}

.hero-content button {
  background: #d10505;
  border: none;
  padding: 1rem 3rem;
  font-size: 1.25rem;
  font-weight: 700;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.3s ease;
  color: white;
}

.hero-content button:hover {
  background: #a00303;
}

/* Features Section */
.features {
  display: flex;
  justify-content: space-around;
  padding: 4rem 2rem;
  background: #fff;
  text-align: center;
  flex-wrap: wrap;
  gap: 2rem;
}

.feature {
  flex: 1 1 250px;
  max-width: 300px;
}

.icon {
  font-size: 3rem;
  color: #d10505;
  margin-bottom: 1rem;
}

.feature h3 {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
}

.feature p {
  color: #444;
  font-size: 1rem;
}

/* About Section */
.about {
  max-width: 800px;
  margin: 0 auto 4rem auto;
  padding: 0 1rem;
  text-align: center;
}

.about h2 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  color: #111;
}

.about p {
  font-size: 1.2rem;
  color: #333;
  line-height: 1.6;
}

/* Responsive */
@media (max-width: 768px) {
  .hero-content h1 {
    font-size: 2.5rem;
  }
  .hero-content p {
    font-size: 1.2rem;
  }
  .features {
    flex-direction: column;
    align-items: center;
  }
}
</style>
