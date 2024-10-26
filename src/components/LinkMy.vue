<template>
  <div class="links">
    <nav class="link__box" v-for="(item, itemIndex) in links" :key="itemIndex">
      <h3 class="link__title">{{ item.title }}</h3>
      <a @click="$emit('setPage', 'Quiz')" class="link" href="#" v-for="(link, linkIndex) in item.links" :key="linkIndex">{{ link }}</a>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'LinkMy',
  data() {
    return {
      
      links: [
          {
          title: "Quick Links",
          links: ['Home', 'About', 'Quiz', 'Contact']
          },
          {
          title: "Explore More",
          links: ['FAQ', 'Gallery', 'Events', 'Blog']
          },
          {
          title: "Connect with Us",
          links: ['Facebook', 'Twitter', 'Instagram', 'LinkedIn']
          }
      ]
    }
  }
}
</script>

<style>
  .links {
    display: flex;
    justify-content: space-between;
    width: 40%;
    gap: 20px;
  }
  .link__box {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }
  .link__title {
    font-size: 16px;
  }
  .link {
    font-size: 16px;
  }
  @media (max-width: 365px) {
    .links {
      align-items: center;
      flex-direction: column;
      gap: 40px;
    }
    .link__box {
      align-items: center;
    }
  }
</style>