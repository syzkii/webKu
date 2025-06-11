<template>
  <button
    v-show="isScrolled"
    @click="scrollToTop"
    id="myBtn"
    title="Go to top"
  >
    <i class="fas fa-chevron-up" aria-hidden="true"></i>
  </button>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const isScrolled = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 300;
};

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: "smooth" });
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped>
#myBtn {
  display: block;
  position: fixed;
  bottom: 20px;
  right: 30px;
  z-index: 99;
  font-size: 18px;
  border: none;
  outline: none;
  background-color: #333;
  color: white;
  cursor: pointer;
  padding: 10px 15px;
  border-radius: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
}

#myBtn:hover {
  background-color: #555;
}

#myBtn i {
  font-size: 1em;
}
</style>