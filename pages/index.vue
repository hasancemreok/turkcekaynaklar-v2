<template>
  <ContentsList />
</template>

<script>
import ContentsList from '@/components/ContentsList.vue';

export default {
  name: 'Index',
  components: {
    ContentsList
  },
  head() {
    return {
      title: 'Türkçe Kaynaklar',
      meta: [
        { hid: 'description', name: 'description', content: 'Yazılım Geliştirme, Web Tasarım, Mobil Uygulama Geliştirme ve diğer konularda özenle seçilmiş Türkçe kaynaklar listesi' },
        { name: 'keywords', content: 'yazılım geliştirme, yazılım eğitimi, web tasarım, mobil uygulama geliştirme, javascript eğitimi, css eğitimi' }
      ],
    }
  }
};
</script>
