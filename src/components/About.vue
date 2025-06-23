<template>
  <main class="about-page">
    <!-- Hero Section -->
    <section class="hero-section">
      <img
        src="https://i0.wp.com/www.muscleandfitness.com/wp-content/uploads/2016/02/jeremy-lat-pulldowns.jpg?quality=86&strip=all"
        alt="Jeff Nippard demonstrating a lat pulldown exercise"
        class="hero-image"
        loading="lazy"
      />
      <h1 class="hero-title">About WolfRep</h1>
    </section>

    <!-- Intro Section -->
    <section class="intro-section container">
      <div class="intro-text">
        <p>
          Wolfrep Fitness is a leading online platform dedicated to providing reliable, science-based information on strength training, bodybuilding, and overall fitness. With a mission to equip athletes and fitness enthusiasts with the best tools and knowledge, Wolfrep Fitness offers in-depth articles, training programs, nutrition advice, and product reviews—all grounded in evidence-based research.

          The team behind Wolfrep Fitness consists of experienced coaches, scientists, and athletes committed to promoting a healthy and sustainable approach to training and nutrition. The platform strongly emphasizes natural strength training and focuses on maximizing performance without the use of banned substances.

          In addition to educational content, Wolfrep Fitness features inspiring success stories and interviews with top athletes and experts in the fitness community. This makes it a valuable resource for anyone serious about improving body composition, strength, and overall health.

          Based in the Netherlands, Wolfrep Fitness continues to grow in popularity thanks to its combination of deep knowledge, practical experience, and an accessible communication style. The platform serves as a trusted guide for beginners and advanced athletes alike who strive for optimal results in a responsible way.
        </p>
      </div>
      <div class="intro-image">
        <img
          src="https://cdn.shopify.com/s/files/1/1633/7705/files/Chris_Bumstead_supplements_480x480.jpg?v=1658503246"
          alt="Jeff Nippard Profile"
          loading="lazy"
        />
      </div>
    </section>

    <!-- Team Section -->
    <section class="team-section container">
      <h2>Meet the Team</h2>
      <div class="team-grid">
        <div class="team-member">
          <img
            src="https://jeffnippard.com/cdn/shop/files/max-edsey.jpg?v=1713836812&width=400"
            alt="Max Edsey"
            loading="lazy"
          />
          <h3>Max Edsey</h3>
          <p>
            Max completed his undergraduate studies in Exercise Science at The Ohio State University, Class of 2018, where he also was a research assistant in Dr. William Kraemer’s lab. Afterward, he traveled to England where he earned his master’s degree in Sport and Exercise Nutrition from Loughborough University. Max began his work for Jeff in Spring of 2017 and currently serves as Jeff's Senior Content Manager.
          </p>
        </div>

        <div class="team-member">
          <img
            src="https://jeffnippard.com/cdn/shop/files/patrick-macinnis.jpg?v=1713836812&width=400"
            alt="Patrick MacInnis"
            loading="lazy"
          />
          <h3>Patrick MacInnis</h3>
          <p>
            Patrick MacInnis is a professional natural men’s physique competitor along with being a certified bodybuilding judge. Patrick is full time online fitness coach and has passion for evidence based fitness both as a coach & a competitor.
            Patrick turned pro in 2016 at the Natural Muscle Mayhem and won his most recent pro show at the Washington State Natural where he was coached by Jeff Nippard. Currently he is training towards hitting the stage again for his debut at Worlds.
          </p>
        </div>

        <div class="team-member">
          <img
            src="https://jeffnippard.com/cdn/shop/files/denise-henstride.jpg?v=1713833982&width=800"
            alt="Denise Henstridge"
            loading="lazy"
          />
          <h3>Denise Henstridge B.Ed. E , ECITS PTC</h3>
          <p>
            Denise has adopted a lifestyle of healthy living for more than 25 years and has been a certified personal coach since May 2006. As an entrepreneur, she established a vibrantly, successful fitness business from 2009-2015.
            As a previous school teacher, she is meticulously organized and efficient, allowing her the advantage of having a great administrative skill set.
            Some of Denise’s personal fitness interests include weight training, biking, swimming, paddle boarding, golfing, downhill skiing and hiking. She enjoys reading, traveling, and spending time with family and friends.
          </p>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  name: "AboutPage",
  metaInfo() {
    return {
      title: 'About WolfRep - WolfRep Fitness',
      meta: [
        {
          name: 'description',
          content: 'WolfRep Fitness is een toonaangevend platform voor evidence-based fitness informatie en training.'
        },
        {
          name: 'viewport',
          content: 'width=device-width, initial-scale=1'
        },
        {
          property: 'og:title',
          content: 'About WolfRep - WolfRep Fitness'
        },
        {
          property: 'og:description',
          content: 'Ontdek alles over WolfRep Fitness, ons team en onze missie.'
        },
        {
          property: 'og:image',
          content: 'https://i0.wp.com/www.muscleandfitness.com/wp-content/uploads/2016/02/jeremy-lat-pulldowns.jpg?quality=86&strip=all'
        }
      ]
    }
  }
}
</script>

<style scoped>
/* ... Jouw bestaande CSS-styling hier ... */
.about-page {
  font-family: 'Helvetica Neue', Arial, sans-serif;
  color: #222;
  line-height: 1.6;
}

/* Container for content */
.container {
  max-width: 1100px;
  margin: 0 auto;
  padding: 2rem 1rem;
}

/* Hero */
.hero-section {
  position: relative;
  text-align: center;
  margin-bottom: 4rem;
}

.hero-image {
  width: 40%;
  max-height: 900px;
  margin-top: 50px;
  object-fit: cover;
  filter: brightness(70%);
  border-radius: 50px;
}

.hero-title {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: #fff;
  font-size: 3rem;
  font-weight: 700;
  text-shadow: 0 2px 8px rgba(0, 0, 0, 0.8);
  user-select: none;
  pointer-events: none;
  margin: 0;
  padding: 0;
}

/* Intro Section */
.intro-section {
  display: flex;
  gap: 3rem;
  align-items: center;
  margin-bottom: 5rem;
  flex-wrap: wrap;
}

.intro-text {
  flex: 1 1 400px;
  font-size: 1.1rem;
  color: #333;
}

.intro-text p {
  margin-bottom: 1rem;
}

.intro-image {
  flex: 0 0 300px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.15);
}

.intro-image img {
  width: 100%;
  height: auto;
  display: block;
}

/* Team Section */
.team-section h2 {
  font-size: 2.5rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 3rem;
  color: #d32f2f;
}

.team-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 3rem;
}

.team-member {
  background: #fafafa;
  border-radius: 10px;
  padding: 1rem 1.5rem 2rem;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.08);
  text-align: center;
  transition: box-shadow 0.3s ease;
}

.team-member:hover {
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15);
}

.team-member img {
  border-radius: 50%;
  width: 140px;
  height: 140px;
  object-fit: cover;
  margin-bottom: 1rem;
  border: 4px solid #d32f2f;
}

.team-member h3 {
  margin: 0.5rem 0 1rem;
  font-weight: 700;
  color: #d32f2f;
}

.team-member p {
  font-size: 0.95rem;
  color: #555;
  line-height: 1.4;
}

/* Responsive */
@media (max-width: 1024px) {
  .hero-image {
    width: 60%;
    max-height: 600px;
    margin-top: 30px;
  }
  
  .intro-section {
    gap: 2rem;
  }
  
  .team-grid {
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  }
}

@media (max-width: 768px) {
  .intro-section {
    flex-direction: column;
  }
  
  .intro-image {
    margin: 2rem auto 0;
    flex: none;
    width: 100%;
    max-width: 320px;
  }
}

@media (max-width: 480px) {
  .hero-image {
    width: 90%;
    max-height: 400px;
    margin-top: 20px;
  }
  
  .intro-text {
    font-size: 1rem;
  }
  
  .team-member img {
    width: 100px;
    height: 100px;
    border-width: 3px;
  }
  
  .team-member h3 {
    font-size: 1.1rem;
  }
  
  .team-member p {
    font-size: 0.9rem;
  }
}
</style>
