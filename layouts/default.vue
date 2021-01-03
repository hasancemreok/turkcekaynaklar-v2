<template>
  <div>
    <Jumbotron :mode=false />
    <Nuxt class="mt-24rem" />
    <Footer />
  </div>
</template>

<script>
import Jumbotron from '@/components/Jumbotron.vue';
import Footer from '@/components/Footer.vue';

export default {
  components: {
    Jumbotron,
    Footer        
  },
  methods: {
    setOnScroll() {
      var jumbotron = document.getElementById("jumbotron");
      var xcontainer = document.getElementById("x-container");

      window.onscroll = function(e) {
        if(window.scrollY) {
          if(window.pageYOffset > 24) {
            jumbotron.classList.add('scrolled');
            xcontainer.className = "x-container mt-6rem";
          } else if (window.pageYOffset <= 23) {
            jumbotron.classList.remove('scrolled')
            xcontainer.className = "x-container mt-24rem";
          }
        }
      }
    }
  },
  mounted() {
    this.setOnScroll();
  },
  destroyed() {
    window.onscroll = null;
  }
}
</script>

<style lang="scss" scoped>
</style>
