<template>
  <img class="bunner" src="@/assets/bunner.png" alt="">
  <h1 class="bunner__title">Welcome to Karlův<br>Most Praha</h1>
  <div class="bunner__box">
    <p class="bunner__text">Explore the rich history and stunning architecture of the iconic Karlův Most, a beloved landmark in the heart of Prague</p>
    <button class="bunner__button" id="btn1">Learn More</button>
  </div>
  <button class="bunner__button" id="btn2">Learn More</button>
</template>

<script>
export default {
  name: 'BunnerMy',

}
</script>

<style>
  .bunner {
    position: relative;
    width: 100%;
  }
  .bunner__title {
    position: absolute;
    top: 70px;
    left: 30%;
  }
  .bunner__box {
    display: flex;
    position: absolute;
    top: 200px;
    flex-direction: column;
    left: 50%;
  }
  .bunner__text {
    font-size: 18px;
    max-width: 365px;
  }
  .bunner__button {
    margin-top: 4vw;
    width: 186px;
  }
  #btn2 {
    margin: auto;
    display: none;
  }
  @media (max-width: 1365px) {
    .bunner__title {
      font-size: 36px;
    }
  }
  @media (max-width: 768px) {
    .bunner__title {
      font-size: 24px;
    }
    .bunner__text {
      display: none;
    }
  }
  @media (max-width: 365px) {
    #btn1 {
      display: none;
    }
    #btn2 {
      display: block;
    }
  }
</style>