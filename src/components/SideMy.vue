<template>
  <nav class="side">
    <a class="side__link" href="#">Discover the Beauty</a>
    <a class="side__link" href="#">Unwind and Relax</a>
    <a class="side__link" href="#">Embrace Innovation</a>
    <a class="side__link" href="#">Timeless Elegance</a>
  </nav>
</template>

<script>
export default {
  name: 'SideMy',

}
</script>

<style>
  .side {
    margin: 80px 0px ;
    display: flex;
    flex-direction: column;
    gap: 40px;
  }
  @media (max-width: 768px) {
    .side {
      display: none;
    }
  }
</style>