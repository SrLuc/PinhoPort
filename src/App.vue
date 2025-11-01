<script setup>
import { ref, onMounted } from "vue";
import Card from "./components/Card.vue";

const THEME_KEY = "site_theme";
const theme = ref(localStorage.getItem(THEME_KEY) || "light");

function applyTheme(t) {
  document.body.classList.toggle("dark", t === "dark");
}

function toggleTheme() {
  theme.value = theme.value === "dark" ? "light" : "dark";
  applyTheme(theme.value);
  localStorage.setItem(THEME_KEY, theme.value);
}

function scrollDown() {
  window.scrollBy({ top: window.innerHeight * 0.9, behavior: "smooth" });
}

onMounted(() => applyTheme(theme.value));

// Contatos
const whatsappNumberDisplay = "99 7684-4836";
const whatsappNumberLink = "55997684836";
const email = "pinho.mateus@icloud.com";
const mapsQuery = "Recife PE";
</script>

<template>
  <main class="container fade-in">
    <div class="bg-anim" aria-hidden="true"></div>

    <div class="header slide-down">
      <img class="eu" src="/assets/eu.png" alt="Mateus" />
      <h1 id="name">Mateus Pinho</h1>
      <p class="bio">
        Personal Trainer especializado em fortalecimento para corredores
      </p>

      <div class="social-contacts">
        <a
          :href="`https://wa.me/${whatsappNumberLink}`"
          class="contact"
          target="_blank"
        >
          <i class="fab fa-whatsapp"></i>
          <span>📱 {{ whatsappNumberDisplay }}</span>
        </a>
        <a :href="`mailto:${email}`" class="contact">
          <i class="far fa-envelope"></i> <span>📧 {{ email }}</span>
        </a>
        <a
          :href="`https://www.google.com/maps/search/?api=1&query=${encodeURIComponent(
            mapsQuery
          )}`"
          target="_blank"
          class="contact"
        >
          <i class="fas fa-map-marker-alt"></i> <span>📍 Recife - PE</span>
        </a>
        <span class="contact"
          ><i class="fas fa-globe"></i> 🌎 Consultoria online</span
        >
        <span class="contact"
          ><i class="fas fa-globe"></i> 🏅 Athletic Lab Nível 1</span
        >

        <span class="contact"
          ><i class="fas fa-globe"></i>🏅 FMS 1</span
        >

        <span class="contact"
          ><i class="fas fa-globe"></i>🏅 CFSC</span
        >
      </div>

      <div class="socials">
        <a href="#"><i class="fab fa-instagram"></i></a>
        <a href="#"><i class="fab fa-whatsapp"></i></a>
        <a href="#"><i class="far fa-envelope"></i></a>
        <a href="#"><i class="fab fa-youtube"></i></a>
      </div>
    </div>

    <div class="links fade-in">

         <a
        target="_blank"
        href="https://wa.me/55997684836"
        class="link"
      >
        <img class="link-img" src="/assets/corrida.png" alt="" />
        <span class="link-text">Agendar Avaliação</span>
      </a>

      <a
        target="_blank"
        href="https://docs.google.com/forms/d/e/1FAIpQLSeQf52bKYTtCOIceTeeHrgHic4xjuaCWffknhH6T-5WcjOYMQ/viewform"
        class="link"
      >
        <img class="link-img" src="/assets/musculo.png" alt="" />
        <span class="link-text">Anamnese - Musculação</span>
      </a>


    </div>

    <Card
      title="Planilha de Corrida"
      text="Plano personalizado."
      imgSrc="/assets/img1.jpg"
    />
    <Card
      title="Consultoria Online"
      text="Treinos ajustados semanalmente."
      imgSrc="/assets/img2.JPG"
    />

    <footer>© 2025 Mateus Pinho • Todos os direitos reservados</footer>
  </main>

  <button class="floating-more" @click="scrollDown">
    <span class="dot"></span> Mais
  </button>

  <div class="floating-controls">
    <button
      @click="toggleTheme"
      :title="theme === 'dark' ? 'Tema Escuro' : 'Tema Claro'"
    >
      <i :class="theme === 'dark' ? 'fas fa-moon' : 'fas fa-sun'"></i>
    </button>
  </div>
</template>

<style>
/* ===== RESET ===== */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Inter", sans-serif;
}

/* ===== BODY ===== */
body {
  background: #f5f6f7;
  color: #202124;
  transition: 0.3s;
  display: flex;
  justify-content: center;
  padding: 20px;
}
body.dark {
  background: #1b1b1b;
  color: #e8eaed;
}

/* ===== CONTAINER ===== */
.container {
  background: #fff;
  max-width: 600px;
  width: 100%;
  padding: 40px 30px;
  border-radius: 28px;
  box-shadow: 0 6px 25px rgba(0, 0, 0, 0.15);
  text-align: center;
  position: relative;
  transition: 0.3s;
}
body.dark .container {
  background: #282a2d;
}

/* ===== HEADER ===== */
.eu {
  width: 140px;
  height: 140px;
  border-radius: 50%;
  box-shadow: 0 15px 25px rgba(0, 0, 0, 0.15), 0 5px 10px rgba(0, 0, 0, 0.05);
}
.bio {
  color: #5f6368;
  margin-bottom: 15px;
}
body.dark .bio {
  color: #ccc;
}

/* ===== SOCIALS ===== */
.socials {
  display: flex;
  justify-content: center;
  gap: 18px;
  margin-bottom: 30px;
}
.socials a {
  color: #5f6368;
  font-size: 1.4rem;
  transition: 0.3s;
}
.socials a:hover {
  color: #1a73e8;
}
body.dark .socials a {
  color: #ccc;
}

/* ===== CONTATOS ===== */
.social-contacts .contact {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  padding: 6px 10px;
  border-radius: 999px;
  background: rgba(0, 0, 0, 0.03);
  color: inherit;
  text-decoration: none;
  box-shadow: 0 1px 6px rgba(0, 0, 0, 0.06);
  margin: 3px;
}
body.dark .social-contacts .contact {
  background: rgba(255, 255, 255, 0.05);
  color: #e8eaed;
}

/* ===== LINKS ===== */
.links {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 20px;
}
.link {
  display: flex;
  align-items: center;
  text-decoration: none;
  background: #f5f5f5;
  border-radius: 10px;
  padding: 0.8rem 1rem;
  transition: 0.3s;
  box-shadow: rgba(0, 0, 0, 0.2) 0 2px 8px;
}
.link:hover {
  background: #e0e0e0;
  transform: translateY(-2px);
}
body.dark .link {
  background: #3c4043;
}
body.dark .link:hover {
  background: #5f6368;
}
.link-img {
  width: 50px;
  height: 50px;
  border-radius: 8px;
  object-fit: cover;
  margin-right: 1rem;
}
.link-text {
  flex: 1;
  font-size: 1rem;
  color: #333;
}

/* ===== CARDS ===== */
.card {
  display: flex;
  align-items: center;
  background: #f5f5f5;
  border-radius: 12px;
  padding: 1rem;
  margin: 10px 0;
  box-shadow: rgba(0, 0, 0, 0.24) 0 3px 8px;
  transition: 0.3s;
}
.card:hover {
  background: #e0e0e0;
}
body.dark .card {
  background: #383b3f;
  color: #e8eaed;
}
.card-img {
  width: 180px;
  height: 150px;
  border-radius: 10px;
  object-fit: cover;
  margin-right: 1rem;
}
.card-content {
  flex: 1;
}
.card-content h3 {
  font-size: 1.1rem;
  color: #222;
  margin-bottom: 0.3rem;
}
body.dark .card-content h3 {
  color: #e8eaed;
}
.card-content p {
  color: #555;
  font-size: 0.95rem;
  line-height: 1.4;
}
body.dark .card-content p {
  color: #ccc;
}

/* ===== FOOTER ===== */
footer {
  margin-top: 30px;
  font-size: 0.8rem;
  color: #777;
}
body.dark footer {
  color: #9aa0a6;
}

/* ===== FLOATING BUTTONS ===== */
.floating-controls button,
.floating-more {
  transition: 0.3s;
  cursor: pointer;
  border: none;
  border-radius: 50px;
  padding: 8px 12px;
}
.floating-controls button {
  background: #fff;
  color: #111;
}
body.dark .floating-controls button {
  background: #303134;
  color: #e8eaed;
}
.floating-more {
  background: #fff;
  color: #111;
  position: fixed;
  bottom: 20px;
  right: 20px;
}
body.dark .floating-more {
  background: #2b2b2b;
  color: #e8eaed;
}

.floating-more {
  position: fixed;
  bottom: 20px; /* distancia do rodapé da tela */
  left: 50%; /* centraliza horizontalmente */
  transform: translateX(-50%); /* ajusta a centralização */
  width: 100px;
  text-align: center;
  background: #fff;
  color: #111;
  padding: 12px 24px;
  border-radius: 30px;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.4); /* sombra mais escura */
  font-weight: bold;
  cursor: pointer;
  border: none;
  transition: transform 0.3s ease, box-shadow 0.3s ease, background 0.3s ease;
  z-index: 100;

  display: flex;
  align-items: center;
  gap: 10px;

  animation: slideUp 0.8s ease forwards; /* animação de entrada */
}

/* Hover / efeito de pressão */
.floating-more:hover {
  transform: translateX(-50%) translateY(-3px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.5);
  background: #f0f0f0;
}

/* Tema escuro */
body.dark .floating-more {
  background: #2b2b2b;
  color: #e8eaed;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.7);
}

body.dark .floating-more:hover {
  background: #3c3c3c;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.8);
}

/* Animação de entrada */
@keyframes slideUp {
  0% {
    transform: translateX(-50%) translateY(40px);
    opacity: 0;
  }
  100% {
    transform: translateX(-50%) translateY(0);
    opacity: 1;
  }
}

/* ===== ANIMAÇÕES ===== */
.fade-in {
  opacity: 0;
  animation: fadeIn 0.8s ease forwards;
}
.slide-down {
  transform: translateY(-15px);
  opacity: 0;
  animation: slideDown 0.8s ease forwards;
}
@keyframes fadeIn {
  to {
    opacity: 1;
  }
}
@keyframes slideDown {
  to {
    transform: translateY(0);
    opacity: 1;
  }
}

/* ===== RESPONSIVO ===== */
@media (max-width: 480px) {
  .container {
    padding: 25px 18px;
    border-radius: 22px;
  }
  .link {
    font-size: 0.95rem;
  }
  .card-content p {
    font-size: 0.85rem;
  }
}
</style>
