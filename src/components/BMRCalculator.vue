<template>
  <section class="bmr-section">
    <h2>Calculate Your BMR</h2>
    <form @submit.prevent="calculateBMR">
      <div class="form-group">
        <label for="age">Age</label>
        <input id="age" type="number" v-model.number="age" required />
      </div>
      <div class="form-group">
        <label for="gender">Gender</label>
        <select id="gender" v-model="gender" required>
          <option value="">Select</option>
          <option value="male">Male</option>
          <option value="female">Female</option>
        </select>
      </div>
      <div class="form-group">
        <label for="height">Height (cm)</label>
        <input id="height" type="number" v-model.number="height" required />
      </div>
      <div class="form-group">
        <label for="weight">Weight (kg)</label>
        <input id="weight" type="number" v-model.number="weight" required />
      </div>
      <button type="submit">Calculate</button>
    </form>

    <div v-if="bmr !== null" class="bmr-result">
      <p>Your BMR is <strong>{{ bmr }}</strong> calories/day</p>

      <div class="form-group">
        <label>Activity Level</label>
        <select v-model="activityLevel">
          <option value="">Select</option>
          <option value="1.2">Sedentary (little or no exercise)</option>
          <option value="1.375">Lightly active (1–3 days/week)</option>
          <option value="1.55">Moderately active (3–5 days/week)</option>
          <option value="1.725">Very active (6–7 days/week)</option>
          <option value="1.9">Super active (twice daily training)</option>
        </select>
      </div>

      <div v-if="tdee !== null">
        <p><strong>Maintenance Calories:</strong> {{ tdee }} kcal/day</p>
        <p><strong>To Lose Fat:</strong> {{ tdee - 500 }} kcal/day (est.)</p>
        <p><strong>To Gain Muscle:</strong> {{ tdee + 300 }} to {{ tdee + 500 }} kcal/day</p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'BMRCalculator',
  data() {
    return {
      age: null,
      gender: '',
      height: null,
      weight: null,
      bmr: null,
      tdee: null,
      activityLevel: '',
    };
  },
  watch: {
    activityLevel(newVal) {
      if (newVal && this.bmr !== null) {
        this.tdee = Math.round(this.bmr * parseFloat(newVal));
      } else {
        this.tdee = null;
      }
    }
  },
  methods: {
    calculateBMR() {
      if (this.gender === 'male') {
        this.bmr = Math.round(10 * this.weight + 6.25 * this.height - 5 * this.age + 5);
      } else if (this.gender === 'female') {
        this.bmr = Math.round(10 * this.weight + 6.25 * this.height - 5 * this.age - 161);
      } else {
        this.bmr = null;
      }

      if (this.activityLevel) {
        this.tdee = Math.round(this.bmr * parseFloat(this.activityLevel));
      } else {
        this.tdee = null;
      }
    }
  }
};
</script>

<style scoped>
.bmr-section {
  background: #f8f9fa;
  padding: 2rem;
  border-radius: 1rem;
  max-width: 600px;
  margin: 2rem auto;
  text-align: center;
}

.bmr-section h2 {
  font-size: 1.8rem;
  margin-bottom: 1rem;
}

.form-group {
  margin: 1rem 0;
}

.form-group label {
  display: block;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.form-group input,
.form-group select {
  width: 100%;
  padding: 0.6rem;
  border: 1px solid #ccc;
  border-radius: 6px;
}

button {
  background-color: #000;
  color: #fff;
  padding: 0.8rem 1.5rem;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  margin-top: 1rem;
}

button:hover {
  background-color: #facc15;
  color: #000;
}

.bmr-result {
  margin-top: 1.5rem;
  font-size: 1.2rem;
  font-weight: bold;
}
.bmr-result select {
  margin: 1rem 0;
  padding: 0.6rem;
  border-radius: 6px;
  width: 100%;
}
.bmr-result p {
  margin: 0.5rem 0;
}
</style>
