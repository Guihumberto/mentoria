<template>
  <v-app theme="light">
    <Header />
    <v-main class="main-vue">
      <router-view />
    </v-main>

    <Footer />
  </v-app>
</template>

<script setup>
  import Header from './header.vue';
  import Footer from './footer.vue';
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
  }
  :root{
    --bg-color:#f8fafc;
    --second-bg-color: #94a3b8;
    --text-color: #ededed;
    --main-color: #01003f;
    --second-color: #42c1e8;
  }
  html{
  /* font-size: 62.5%; */
  /* overflow: hidden; */
  }
  .main-vue{
    background: var(--main-color);
    color: white;
  }
  section{
    min-height: calc(100vh - 40px);
    width: min(1080px, 100%);
    margin-inline: auto;
    padding: 2rem;
  }
  .animate{
    position: absolute;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: var(--main-color);
    animation: show-right 1s ease-out forwards;
    animation-delay: calc(.3s * var(--i));
  }

  .animate.bg{
    animation: fade-in 1s ease-out forwards;
    animation-delay: 3.2s;
  }

  @media (max-width: 500px) {
    section{
      min-height: 100vh;
    }
  }

  @keyframes show-right {
    100%{
      width: 0;
    }
  }

  @keyframes fade-in {
    100%{
      opacity: 0;
    }
  }

  /* breakpoints */
  @media (max-width: 1200px) {
    html{
      font-size: 75%;
    }
  }
  
</style>
