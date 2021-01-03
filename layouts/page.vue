<template>
  <div>
    <Jumbotron :mode=true />
    <Nuxt class="mt-6rem" />
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
  }
}
</script>

<style lang="scss" scoped>
</style>
