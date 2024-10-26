<template>
  <Header @setPage="(isPage = $event)"/>
  <div class="row">
    <Side />
    <main>
      <Bunner />
      <History />
      <component :is="isPage === 'Home' ? 'Cards' : 'QuizMy'" />
    </main>
  </div>
  <Footer />
  <svg v-if="showArrow" @click="scrollToTop" class="arrow" id="arrow" width="50" height="50" viewBox="0 0 50 50" fill="none" xmlns="http://www.w3.org/2000/svg">
  <circle cx="25" cy="25" r="24.5" fill="white" stroke="#6E6B70"/>
  <path d="M17 28L25 20L33 28" stroke="#201D1F" stroke-width="3.5" stroke-linecap="square" stroke-linejoin="round"/>
  </svg>
</template>

<script>
import Header  from './components/HeaderMy.vue'
import Side    from './components/SideMy.vue'
import Bunner  from './components/BunnerMy.vue'
import History from './components/HistoryMy.vue'
import Cards   from './components/CardsMy.vue'
import Footer  from './components/FooterMy.vue'
import QuizMy  from './components/QuizMy.vue'

export default {
  name: 'App',
  data() {
    return {
      isPage: 'Home',
      showArrow: false, 
    };
  },
  components: {
    Header,
    Side,
    Bunner,
    History,
    Cards,
    Footer,
    QuizMy
  },
  methods: {
    switchPage() {
      this.isPage = !this.isPage;
    },
    scrollToTop() {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    },
    handleScroll() {
      this.showArrow = window.scrollY > 800; 
    },
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
}
</script>

<style>
 :root {
  --col1: #6E6B70;
  --col2: #524C52;
  --col3: #201D1F;
  --col4: #E44D48;
  --col5: #FEDAD3;
  --col6: #ECECEC;
 }

  h1 {
    font-family: 'Libre Baskerville';
    font-size: 56px;
  }
  h2 {
    font-family: 'Libre baskerville';
    font-size: 32px;
  }
  h3 {
    font-family: 'Libre baskerville';
    font-size: 24px;
  }
  h4 {
    font-family: 'Libre baskerville';
    font-size: 16px;
  }
  nav {
    font-size: 24px;
  }
  p {
    font-family: 'Work Sans';
    font-size: 18px;
  }
  @media(max-width: 1365px) {

  }
  * {
    box-sizing: border-box;
    padding: 0px;
    transition: all 0.3s ease;
    margin: 0px;
  }
  body {
    font-family: "Work Sans", sans-serif;
    transition: all 0.3s ease;
    padding: 0px 40px;
  }
  button {
    background: var(--col4);
    border: none;
    color: var(--col5);
    cursor: pointer;
    padding: 15px 40px;
    font-size: 16px;
  }
  button:hover {
    opacity: 0.6;
  }
  button:active {
    opacity: 0.9;
  }
  .row {
    display: flex;
    gap: 20px;
  }
  .arrow {
    cursor: pointer;
    position: fixed;
    right: 40px;
    bottom: 40px;
  }
  .arrow:hover circle {
    fill: #000;
  }
  .arrow:hover path {
    stroke: #FFF;
  }
  main > * {
    margin: 80px 0px;
  }
  @media (max-width: 365px) {
    body {
      padding: 0px 20px;
    }
    .arrow {
      display: none;
    }
  }
</style>
