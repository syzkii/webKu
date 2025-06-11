<template>
  <section id="main-project" class="section-4">
    <div class="container text-center">
      <h1 class="text-dark">My Projects</h1>
      <p class="text-secondary">
        Visit My Github Profile For More Projects:
        <a :href="`https://github.com/${socials.github}`"><u>Syzkii</u></a>
      </p>
    </div>

    <div class="cards">
      <div class="d-flex flex-wrap justify-content-center gap-3">
        <div
          v-for="(project, index) in projects"
          :key="index"
          class="card shadow-lg project-card"
          style="width: 18rem"
          data-aos="zoom-in-left"
        >
          <img
            :src="project.image"
            width="200px"
            height="30%"
            class="card-img-top"
            :alt="project.alt"
          />
          <div class="card-body">
            <h4 class="card-title">{{ project.title }}</h4>
            <p class="card-text">{{ project.description }}</p>
          </div>
          <div class="card-body">
            <a
              v-if="project.github"
              :href="project.github"
              target="_blank"
              class="card-link btn btn-dark"
              >Github Project <i class="fab fa-github"></i
            ></a>
          </div>
          <div v-if="project.demo" class="card-body">
            <a
              :href="project.demo"
              target="_blank"
              class="card-link btn btn-primary"
              >Demo Website <i class="fa fa-info-circle"></i
            ></a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
defineProps({
  projects: {
    type: Array,
    required: true,
  },
  socials: {
    type: Object,
    required: true,
  },
});
</script>

<style scoped>
.project-card {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.project-card:hover {
  transform: translateY(-10px) scale(1.05);
  box-shadow: 0 1rem 1.5rem rgba(0, 0, 0, 0.2) !important;
  z-index: 10;
}
</style>