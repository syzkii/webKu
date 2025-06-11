<template>
  <div id="app">
    <GoToTopButton />
    <Header :personalInfo="personalInfo" />
    <About
      :personalInfo="personalInfo"
      :training="training"
      :education="education"
      :skills="skills"
    />
    <section class="section-3 container-fluid p-0">
      <div class="container-fluid text-center">
        <div
          class="numbers d-flex flex-md-row flex-wrap justify-content-center"
        ></div>
      </div>
    </section>
    <Projects :projects="projects" :socials="socials" />
    <Contact />
    <Footer :personalInfo="personalInfo" :socials="socials" :currentYear="currentYear" />
  </div>
</template>

<script setup>
import Header from './pages/Header.vue';
import About from './pages/About.vue';
import Projects from './pages/Projects.vue';
import Contact from './pages/Contact.vue';
import Footer from './pages/Footer.vue';
import GoToTopButton from './pages/GoToTopButton.vue';
import { reactive, onMounted } from 'vue';
import AOS from "aos";
import "aos/dist/aos.css";

// Data Reaktif (pindahkan dari App.vue)
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
    "Vue Js",
    "React Js (learning)",
    "MySQL",
    "Laravel",
  ],
  tools: ["Git", "Bootstrap", "Github", "VSCode", "Tailwind CSS", "Linux"],
});

const projects = reactive([
  {
    image: "/proj1.webp",
    alt: "Foto Crud Login Session Dynamic",
    title: "CRUD Login Session Dynamic",
    description:
      "Created using technologies like PHP, HTML5, CSS3, BOOTSTRAP v4.3 and JavaScript.",
    github: "https://github.com/syzkii/login-dinamis",
    demo: null,
  },
  {
    image: "/proj1.webp",
    alt: "Foto Crud Login Session Static",
    title: "CRUD Login Session Static",
    description:
      "Created using technologies like PHP, HTML 5, CSS3, BOOTSTRAP v4.3 and JavaScript.",
    github: "https://github.com/syzkii/login-statis",
    demo: null,
  },
  {
    image: "/proj1.webp",
    alt: "Website Crud Login Session Admin dan Operator",
    title: "CRUD Login Session Admin & Operator",
    description:
      "Created using technologies like PHP, HTML5, CSS3, BOOTSTRAP v4.3 and JavaScript.",
    github: "https://github.com/syzkii/login-admin-operator",
    demo: null,
  },
  {
    image: "/proj2.webp",
    alt: "Website Karang Taruna Green Hill",
    title: "Karang Taruna Project",
    description:
      "Created using technologies like PHP, CSS3, BOOTSTRAP v4.3 and JavaScript.",
    github: "https://github.com/syzkii/KarangTarunaProject",
    demo: "https://karangtarunagh.000webhostapp.com/",
  },
  {
    image: "/Ramgan.webp",
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

onMounted(() => {
  // Inisialisasi AOS
  AOS.init();
});
</script>

<style>
/* Letakkan isi dari file CSS Anda di sini (src/style.css dan src/mobile-style.css).
  Gunakan <style scoped> jika Anda ingin gaya ini hanya berlaku untuk komponen ini.
  CSS dari Bootstrap dan FontAwesome harus diimpor secara global di main.js atau di-link di index.html.
*/

/* Contoh: Beberapa gaya dasar dari HTML asli */
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