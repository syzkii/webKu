<template>
  <div id="app">
    <button
      v-show="isScrolled"
      @click="scrollToTop"
      id="myBtn"
      title="Go to top"
    >
      <i class="fa fa-chevron-up" aria-hidden="true"></i>
    </button>

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
              src="/frontend/assets/Programmer-Engineering-Development-Illustration-on-transparent-background-PNG.webp"
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

    <section id="main-about" class="section-2">
      <div class="container text-center">
        <div class="row">
          <div class="col-md-6 col-12">
            <div class="pray">
              <img
                src="/frontend/assets/kiki.webp"
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

    <section class="section-3 container-fluid p-0">
      <div class="container-fluid text-center">
        <div
          class="numbers d-flex flex-md-row flex-wrap justify-content-center"
        ></div>
      </div>
    </section>

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

    <section id="main-contact" class="section-5">
      <div class="contact">
        <div class="form-container">
          <h2>Contact Me</h2>
          <form method="POST" action="https://formspree.io/f/xeqvkzbo">
            <div class="input-field">
              <input id="name" type="text" required />
              <label for="name">Name*</label>
            </div>
            <div class="input-field">
              <input id="email" type="email" required />
              <label for="email">Email*</label>
            </div>
            <div class="input-field">
              <textarea id="messages" rows="5" required></textarea>
              <label for="messages">Messages*</label>
            </div>
            <button type="submit" class="btn">Send</button>
          </form>
        </div>
      </div>
      <div class="quote">
        <h4>
          “Your most unhappy customers are your greatest source of learning.”
          <br /><br /><b>~ Bill Gates ~</b>
        </h4>
      </div>
    </section>

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
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, reactive } from "vue";
import AOS from "aos";

// --- Data Reaktif ---
const personalInfo = reactive({
  name: "Rifki Ardian Akbar",
  nickname: "Kiki",
  role: "Web Developer",
  favoriteLanguages: ["PHP", "JavaScript"],
  phone: "6281615304956",
  email: "rifkiardianakbar.raa@gmail.com",
  bio: "I'm a passionate learner who's always willing to learn and work across technologies and domains.",
});

const training = reactive([
  "Junior Network Administrator - KOMINFO",
  "Digital Enterpreneurship Academy - KOMINFO",
]);

const education = reactive([
  { school: "SMKS SEMEN GRESIK", years: "2018-2021" },
  { school: "SMPN 2 KEBOMAS", years: "2015-2018" },
  { school: "SDN 2 RANDUAGUNG", years: "2009-2015" },
]);

const skills = reactive({
  tech: [
    "C++",
    "Javascript",
    "Python",
    "HTML5",
    "CSS3",
    "jQuery",
    "PHP",
    "Vue Js (learning)",
    "React Js (learning)",
    "MySQL",
  ],
  tools: ["Git", "Bootstrap", "Github", "VSCode", "Tailwind CSS", "Linux"],
});

const projects = reactive([
  {
    image: "proj1.webp",
    alt: "Foto Crud Login Session Dynamic",
    title: "CRUD Login Session Dynamic",
    description:
      "Created using technologies like PHP, HTML5, CSS3, BOOTSTRAP v4.3 and JavaScript.",
    github: "https://github.com/syzkii/login-dinamis",
    demo: null,
  },
  {
    image: "proj1.webp",
    alt: "Foto Crud Login Session Static",
    title: "CRUD Login Session Static",
    description:
      "Created using technologies like PHP, HTML 5, CSS3, BOOTSTRAP v4.3 and JavaScript.",
    github: "https://github.com/syzkii/login-statis",
    demo: null,
  },
  {
    image: "proj1.webp",
    alt: "Website Crud Login Session Admin dan Operator",
    title: "CRUD Login Session Admin & Operator",
    description:
      "Created using technologies like PHP, HTML5, CSS3, BOOTSTRAP v4.3 and JavaScript.",
    github: "https://github.com/syzkii/login-admin-operator",
    demo: null,
  },
  {
    image: "proj2.webp",
    alt: "Website Karang Taruna Green Hill",
    title: "Karang Taruna Project",
    description:
      "Created using technologies like PHP, CSS3, BOOTSTRAP v4.3 and JavaScript.",
    github: "https://github.com/syzkii/KarangTarunaProject",
    demo: "https://karangtarunagh.000webhostapp.com/",
  },
  {
    image: "Ramgan.webp",
    alt: "foto website jam tangan",
    title: "Website Jam Tangan",
    description:
      "Created using technologies like HTML, CSS3,BOOTSTRAP v4.3 and JavaScript.",
    github: "#", // Tautan tidak tersedia di HTML asli
    demo: "#", // Tautan tidak tersedia di HTML asli
  },
]);

const socials = reactive({
  github: "syzkii",
  facebook: "ardianrifkia",
  instagram: "ardianrifki_",
  twitter: "ardianrifki_",
});

const currentYear = new Date().getFullYear();

// --- Logika untuk Tombol "Go to Top" ---
const isScrolled = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 300;
};

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: "smooth" });
};

// --- Logika untuk Efek Mengetik (Typewriter) ---
const typewriterElement = ref(null);
const typewriteTexts = [
  "Just an imperfect people",
  "I Love U and Code",
  "hahahaha...",
];
const period = 500;

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

// --- Helper untuk path gambar ---
// Ini mengasumsikan gambar Anda ada di `src/assets/`
const getImageUrl = (name) => {
  return new URL(`./assets/${name}`, import.meta.url).href;
};

// --- Lifecycle Hooks ---
onMounted(() => {
  // Inisialisasi AOS
  AOS.init();

  // Tambahkan event listener untuk scroll
  window.addEventListener("scroll", handleScroll);

  // Mulai efek typewriter
  if (typewriterElement.value) {
    startTypewriter(typewriterElement.value);
  }
});

onUnmounted(() => {
  // Hapus event listener untuk mencegah memory leak
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style>
/* Letakkan isi dari file CSS Anda di sini (src/style.css dan src/mobile-style.css).
  Gunakan <style scoped> jika Anda ingin gaya ini hanya berlaku untuk komponen ini.
  CSS dari Bootstrap dan FontAwesome harus diimpor secara global di main.js atau di-link di index.html.
*/

/* Contoh: Beberapa gaya dasar dari HTML asli */
#myBtn {
  display: block; /* Dikelola oleh v-show di Vue */
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
  border-radius: 4px;
}

#myBtn:hover {
  background-color: #555;
}

/* Target kelas .project-card yang kita tambahkan.
  'transition' membuat semua perubahan properti (transform, box-shadow)
  berjalan mulus selama 0.3 detik.
*/
.project-card {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

/* Ini adalah style yang akan diterapkan SAAT KURSOR DI ATAS CARD.
*/
.project-card:hover {
  /* Efek 'mengangkat' dan 'memperbesar'.
    - translateY(-10px): Menggeser card ke atas sebanyak 10px.
    - scale(1.05): Memperbesar card sebanyak 5%.
  */
  transform: translateY(-10px) scale(1.05);

  /* Mempertegas bayangan agar efek mengangkat lebih terasa.
    Anda bisa menyesuaikan nilai ini sesuai selera.
  */
  box-shadow: 0 1rem 1.5rem rgba(0, 0, 0, 0.2) !important;

  /* Z-index agar card yang di-hover berada di atas yang lain */
  z-index: 10;
}

/* Anda perlu menyalin semua gaya lain dari file CSS Anda ke sini */
</style>
