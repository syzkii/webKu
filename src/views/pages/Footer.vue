<template>
  <footer>
    <div class="container-fluid p-0">
      <div class="row text-left">
        <div class="col-md-9">
          <p class="text-muted">For any suggestion you can mail me</p>
          <p class="gmail">{{ personalInfo.email }}</p>
        </div>
        <div class="col-md-3 follow">
          <h4 class="text-light">Follow Me</h4>
          <p class="text-muted">Let us be social</p>
          <div class="column text-light">
            <a
              :href="`https://www.github.com/${socials.github}`"
              target="_blank"
              ><i class="fab fa-github"></i
            ></a>
            <a
              :href="`https://www.facebook.com/${socials.facebook}`"
              target="_blank"
              ><i class="fab fa-facebook"></i
            ></a>
            <a
              :href="`https://www.instagram.com/${socials.instagram}`"
              target="_blank"
              ><i class="fab fa-instagram"></i
            ></a>
            <a
              :href="`https://www.twitter.com/${socials.twitter}`"
              target="_blank"
              ><i class="fab fa-twitter"></i
            ></a>
          </div>
        </div>
      </div>
    </div>
    <div class="pt-5 text-center">
      <p class="pt-2 text-muted">
        Copyright &copy; {{ currentYear }} All rights reserved. This site is
        made with <i class="fa fa-heart"></i> by
        <a class="sp" :href="`https://github.com/${socials.github}`"
          ><span> Rifki Ardian </span></a
        >
      </p>
    </div>
  </footer>
</template>

<script setup>
defineProps({
  personalInfo: {
    type: Object,
    required: true,
  },
  socials: {
    type: Object,
    required: true,
  },
  currentYear: {
    type: Number,
    required: true,
  },
});
</script>