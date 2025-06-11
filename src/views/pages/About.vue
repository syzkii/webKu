<template>
  <section id="main-about" class="section-2">
    <div class="container text-center">
      <div class="row">
        <div class="col-md-6 col-12">
          <div class="pray">
            <img
              src="/kiki.webp"
              crop="circle"
              width="70%"
              height="40%"
              alt="my-pic"
              data-aos="fade-right"
              data-aos-duration="400"
              data-aos-delay="200"
              data-aos-easing="ease-in-sine"
            />
          </div>
        </div>
        <div class="col-md-6 col-12">
          <div
            class="panel text-left"
            data-aos="zoom-in-left"
            data-aos-delay="300"
            data-aos-duration="500"
          >
            <h2>About</h2>
            <h3>{{ personalInfo.name }}</h3>
            <p>{{ personalInfo.bio }}</p>

            <h3>TRAINING</h3>
            <p v-for="item in training" :key="item">{{ item }}<br /></p>

            <h3>EDUCATION</h3>
            <p v-for="edu in education" :key="edu.school">
              {{ edu.school }} {{ edu.years }}<br />
            </p>

            <h3>SKILLS</h3>
            <p>
              {{ skills.tech.join(", ") }}.
              <br />
              {{ skills.tools.join(", ") }}.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
defineProps({
  personalInfo: {
    type: Object,
    required: true,
  },
  training: {
    type: Array,
    required: true,
  },
  education: {
    type: Array,
    required: true,
  },
  skills: {
    type: Object,
    required: true,
  },
});
</script>