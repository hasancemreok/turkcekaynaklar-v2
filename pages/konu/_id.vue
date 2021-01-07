<template>
  <div class="x-container">
    <!--<div class="sub-nav">
      <NuxtLink to="/">
        <i class="fas fa-arrow-left"></i>
        <span>Geri Dön</span>
      </NuxtLink>
    </div>
    -->
    <div class="topic-header">
      <i class="topic-icon" :class="topic.class"></i>
      <div class="topic-info">
        <h1>{{topic.title}}</h1>
        <span>{{topic.title}} konu başlığına ait içerikler görüntüleniyor</span>
      </div>
    </div>
    <div class="topic-content">
      <div class="content" v-for="(content, index) in contents" :key="'content-' + index">
        <i :class="getContentClass(content.type)"></i>
        <div class="content-info">
          <h3><a target="_blank" :href="content.link">{{content.title}}</a></h3>
          <div class="sub-links">
            <span class="author"><NuxtLink :to="'/yazar/' + content.authorId">{{content.authorName}}</NuxtLink></span>
            <!--<span class="author">&bull;</span>
            <span class="author"><a :href="content.link" target="_blank">{{content.link}}</a></span>-->
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Konu',
  components: { },
  layout: 'page',
  head() {
    return {
      title: `${this.topic.title} - Türkçe Kaynaklar Listesi`,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: `${this.topic.title} için Türkçe yazılım ve tasarım dersleri`
        },
        {
          name: 'keywords',
          content: `${this.topic.title} türkçe kaynaklar yazılım tasarım`
        }
      ]
    }
  },
  data() {
    return {
      contents_Local: [
        { type: "www", author: "Mobilhanem", title: "Mobilhanem", link: "https://www.mobilhanem.com" },
        { type: "www", author: "Yusuf Çakal", title: 'Android Günlüğü', link: "http://yusufcakal.com" },
        { type: "medium", author: "Yusuf Çakal", title: 'Android Uygulamaya "Facebook ile Giriş" Ekleme', link: "https://medium.com/@yusufcakal/android-uygulamaya-facebook-ile-giri%C5%9F-ekleme-14940166eb22" },
        { type: "www", author: "Ümit Köse", title: 'umiitkose.com Android Blog', link: "http://www.umiitkose.com/android" },
        { type: "pdf", author: "Ümit Köse", title: 'Android Türkçe PDF', link: "http://umiitkose.com/wp-content/uploads/2015/08/AndroidStudio.pdf" },
        { type: "youtube", author: "Levent Yadırga", title: 'Android Studio ile Uygulama Geliştirme Eğitimi', link: "https://www.youtube.com/playlist?list=PL9qDMO9EzLX25NTHm0q7svKLx__OZY8-e" },
        { type: "medium", author: "Halil Özel", title: 'Android KTX Nedir ?', link: "https://medium.com/@halilozel1903/android-ktx-nedir-84ecbc615bfb" },
        { type: "medium", author: "Halil Özel", title: 'App Inventor Nedir ?', link: "https://medium.com/@halilozel1903/app-inventor-nedir-c37215ae598a" },
      ],
      contents: null,
      topic: {},
    }
  },
  async fetch() {
    this.topic = await fetch('https://turkcekaynaklar-backend-d6rdc62m6q-ey.a.run.app/api/topics/' + this.$route.params.id)
    .then(response => response.json())
    .then(response => response[0])

    this.contents = await fetch('https://turkcekaynaklar-backend-d6rdc62m6q-ey.a.run.app/api/topics/' + this.$route.params.id + '/resources')
    .then(response => response.json())
  },
  methods: {
    getContentClass(type) {
      if(type === "www") return "fab fa-chrome";
      else if(type === "youtube") return "fab fa-youtube";
      else if(type === "medium") return "fab fa-medium";
      else if(type === "pdf") return "fas fa-file-pdf"
    }
  }
};
</script>

<style lang="scss" scoped>

  .x-container {
    padding-top: 1rem;
    display: flex;
    flex-direction: column;

    /*.sub-nav {
      margin-bottom: 1rem;

      a {
        text-decoration: none;
        display: flex;
        align-items: center;
        color: #02030F;

        i {
          text-align: left;
          font-size: 1rem;
          width: 1rem;
          margin-right: .5rem;
          color: #02030F;
        }
      }
    }*/
  }

  .topic-header {
    display: flex;
    flex-direction: row;
    padding: 1rem 0;
    margin-bottom: 1rem;
    border-bottom: 1px solid var(--c-theme-mid);

    i.topic-icon {
      font-size: 4rem;
      height: auto;
      display: block;
      margin-right: 1rem;
      text-align: left;
    }

    .topic-info {
      display: flex;
      flex-direction: column;
      justify-content: space-around;

      h1 {
        font-weight: 400;
      }

      span {
        color: var(--c-text-secondary);
      }
    }
  }

  .topic-content {

    .content {
      display: flex;
      flex-direction: row;
      align-items: flex-start;
      justify-content: flex-start;
      padding: 1.25rem .5rem;
      border-bottom: 1px solid var(--c-theme-mid);
      
      &:last-child { border: none; }

      &:hover {
        background-color: var(--c-theme-mid);
      }

      i {
        width: 2rem;
        font-size: 2rem;
        margin-right: 1.5rem;
        text-align: center;

        &.fa-youtube { color: red; }
        &.fa-chrome { color: var(--c-ontheme); }
        &.fa-file-pdf { color: #2169a9; }
      }

      .content-info {
        display: flex;
        flex-direction: column;
        justify-content: space-between;

        h3 {
          font-weight: 400;
          margin-bottom: .25rem;

          a { color: var(--c-ontheme); }
        }

        span.author {
          font-size: .875rem;
          color: var(--c-text-secondary);
          
          &:nth-child(2) {
            margin:0 .5rem;
          }

          a { color: var(--c-text-secondary); }
        }

        h3, span {
          a {
            text-decoration: none;
          }

          &:hover {
            a { text-decoration: underline;}
          }
        }
      }
    }
  }

</style>
