<template>
  <section class="cards">
    <div class="card" v-for="(card, index) in cards" :key="index" :class="getCardClass(index)">
      <img class="card__img" src="@/assets/card.png" alt="card">
      <div class="card__box">
        <h3 class="card__title">Unwind and Relax</h3>
        <p class="card__text">Elevate Your Senses</p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'CardsMy',
  data() {
    return {
      cards: Array(6).fill(null),
    }
  },
  methods: {
    getCardClass(index) {
      const isMobile = window.innerWidth < 1050;

      if (isMobile) {
        return index % 2 !== 0 ? 'white-bg' : 'dark-bg';
      }
      return [1, 2, 5].includes(index) ? 'white-bg' : 'dark-bg';
    }
  }
}
</script>

<style>
.card {
  overflow: hidden; /* Или auto, если нужно */
}
  .white-bg {
    background: #FFF;
  }
  .dark-bg {
    background: var(--col6);
  }
  .cards {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
  }
  .card {
    display: flex;
    padding: 40px;
    flex-wrap: wrap;
    gap: 40px;
  }
  .card__img {
    border-radius: 50%;
  }
  .card__title {
    margin-bottom: 10px;
  }
  @media (max-width: 1050px) {
    .cards {
      grid-template-columns: 1fr;
    }
  }
</style>