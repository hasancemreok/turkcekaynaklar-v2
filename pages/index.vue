<template>
  <div>
    <Jumbotron />
    <ContentsList />
  </div>
</template>

<script>
import Jumbotron from '@/components/Jumbotron.vue';
import ContentsList from '@/components/ContentsList.vue';

export default {
  name: 'Index',
  components: {
    Jumbotron,
    ContentsList
  },
};
</script>
