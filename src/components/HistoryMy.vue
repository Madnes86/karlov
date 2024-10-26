<template>
  <section class="history">
    <div class="history__box">
      <h2 class="history__title">Captivating Prague</h2>
      <p class="history__text">Discover the timeless charm of Karlův Most, a beloved Prague landmark that has witnessed the city's evolution over the centuries.<br>
        Experience the Charm of Karlův Most, a beloved Prague landmark that has stood the test of time, connecting the city's past and present with its stunning architecture and rich history. Explore the bridge's intricate details, marvel at the panoramic views, and immerse yourself in the vibrant culture that thrives along its banks</p>
    </div>
    <img class="history__img" src="@/assets/history.png" alt="history">
  </section>
</template>

<script>
export default {
  name: 'HistoryMy',

}
</script>

<style>
  .history {
    display: flex;
    gap: 20px;
  }
  .history__box {
    display: flex;
    flex-direction: column;
    max-width: 928px;
    gap: 40px;
  }
  .history__img {
    max-width: 365px;
    min-width: 158px;
    width: 100%;
  }
  @media (max-width: 768px) {
    .history__title {
      font-size: 28px;
    }
  }
  @media (max-width: 365px) {
    .history {
      flex-direction: column;
    }
    .history__title {
      font-size: 20px;
    }
  }
</style>