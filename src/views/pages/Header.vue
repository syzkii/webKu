<template>
  <header id="main-header">
    <div class="container-fluid p-0">
      <nav class="navbar navbar-expand-lg">
        <a href="#" class="navbar-brand"></a>
        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <i class="fas fa-align-right text-light"></i>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <div class="mr-auto"></div>
          <ul class="navbar-nav">
            <li class="nav-item active">
              <a class="nav-link" href="#main-header"
                >HOME <span class="sr-only">(current)</span></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#main-about">ABOUT</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#main-project">PROJECTS</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#main-contact">CONTACT</a>
            </li>
          </ul>
        </div>
      </nav>
    </div>
    <div class="container text-left header-ctr">
      <div class="row d-flex align-items-center">
        <div
          class="col-md-7 col-sm-12 header-text"
          data-aos="fade-right"
          data-aos-duration="1000"
          data-aos-delay="500"
        >
          <h2>
            #
            <a href="#" class="typewrite" ref="typewriterElement">
              <span class="wrap"></span>
            </a>
          </h2>
          <br />
          <h1>
            Hello I am {{ personalInfo.name }}<br />A.K.A
            {{ personalInfo.nickname }}
          </h1>
          <h5>
            I am a {{ personalInfo.role }}, with
            {{ personalInfo.favoriteLanguages.join(" and ") }} as my favorite
            programming languages.
          </h5>
          <br />
          <div class="text-left">
            <a
              class="button btn btn-light px-5 py-1.5 sayhi"
              style="font-family: roboto"
              :href="`https://api.whatsapp.com/send?phone=${personalInfo.phone}`"
              target="_top"
              >Click me!</a
            >
          </div>
          <br />
        </div>
        <div class="col-md-5 col-sm-12 main-img h-25">
          <img
            src="/Programmer-Engineering-Development-Illustration-on-transparent-background-PNG.webp"
            width="100%"
            height="100%"
            alt="Gambar ilustrasi"
            data-aos="fade-up"
            data-aos-delay="1000"
            data-aos-duration="1000"
          />
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref, reactive, onMounted } from "vue";

// Props
const props = defineProps({
  personalInfo: {
    type: Object,
    required: true,
  },
});

// --- Logika untuk Efek Mengetik (Typewriter) ---
const typewriterElement = ref(null);
const typewriteTexts = [
  "Just an imperfect people",
  "I Love U and Code",
  "hahahaha...",
];
const period = 1000;

const startTypewriter = (el) => {
  let loopNum = 0;
  let txt = "";
  let isDeleting = false;

  function tick() {
    const i = loopNum % typewriteTexts.length;
    const fullTxt = typewriteTexts[i];

    if (isDeleting) {
      txt = fullTxt.substring(0, txt.length - 1);
    } else {
      txt = fullTxt.substring(0, txt.length + 1);
    }

    if (el) {
      el.innerHTML = '<span class="wrap">' + txt + "</span>";
    }

    let delta = 200 - Math.random() * 100;
    if (isDeleting) {
      delta /= 2;
    }
    if (!isDeleting && txt === fullTxt) {
      delta = period;
      isDeleting = true;
    } else if (isDeleting && txt === "") {
      isDeleting = false;
      loopNum++;
      delta = 500;
    }
    setTimeout(tick, delta);
  }
  tick();
};

onMounted(() => {
  if (typewriterElement.value) {
    startTypewriter(typewriterElement.value);
  }
});
</script>