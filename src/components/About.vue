<template>
  <main class="about-page">
    <!-- Hero Section -->
    <section class="hero-section">
      <img
        src="https://i0.wp.com/www.muscleandfitness.com/wp-content/uploads/2016/02/jeremy-lat-pulldowns.jpg?quality=86&strip=all"
        alt="Jeff Nippard"
        class="hero-image"
      />
     
    </section>

    <!-- Intro Section -->
    <section class="intro-section container">
      <div class="intro-text">
        <p>
          Jeff is a professional drug-free bodybuilder and powerlifter.
          Through his informative and entertaining YouTube channel which has gathered a fan-base of almost 7M subscribers, Jeff aims to share the knowledge he has gathered through university education and field experience with others who are passionate about the science behind building muscle, losing fat and getting healthier.
        </p>
        <p>
          He earned the title of Mr. Junior Canada for natural bodybuilding in 2012 and as a powerlifter, Jeff held the Canadian national record for the bench press in 2014. As a powerlifter, Jeff has claimed a 502 lb squat, 336 lb bench press and a 518 lb deadlift with an all time best Wilks score of 446.
        </p>
        <p>
          With a Bachelor of Science degree in biochemistry, Jeff has gathered the requisite scientific knowledge to complement his practical experience acquired through training and coaching. Jeff has coached women’s bikini and men’s bodybuilding national and provincial champions, professional natural bodybuilders and nationally and IPF Worlds qualified raw powerlifters. He has presented seminars on block periodization, concurrent training and nutrition and training for natural bodybuilding in academic settings including the 2014 Online Fitness Summit, the 2019 ultimate evidence-based conference (UEBC) and has guest lectured at the University of Iowa and Lehman College. He has aspirations of completing a PhD in exercise science or a related field.
        </p>
        <p>
          Jeff currently lives in Ontario, Canada where he is producing informative YouTube videos and podcasts.
        </p>
      </div>
      <div class="intro-image">
        <img
          src="https://cdn.shopify.com/s/files/1/1633/7705/files/Chris_Bumstead_supplements_480x480.jpg?v=1658503246"
          alt="Jeff Nippard Profile"
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
};
</script>

<style scoped>
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

.hero-section h1 {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: #fff;
  font-size: 3rem;
  font-weight: 700;
  text-shadow: 0 2px 8px rgba(0, 0, 0, 0.8);
  user-select: none;
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
