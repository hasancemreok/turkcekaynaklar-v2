<template>
  <div class="x-container">
    <div class="topic-header">
      <img class="profile-pic">
      <div class="topic-info">
        <h1>{{author.name}}</h1>
        <p v-if="author.description">{{author.description}}</p>
        <div class="links">
          <span class="profile-link website"><a target="_blank" :href="author.website">{{author.uniqueName}}</a></span>
          <span class="profile-link twitter"><a target="_blank" :href="'https://twitter.com/' + author.twitter">{{author.twitter}}</a></span>
          <span class="profile-link youtube"><a target="_blank" :href="'https://youtube.com/' + author.youtube">{{author.youtube}}</a></span>
          <span class="profile-link github"><a target="_blank" :href="'https://github.com/' + author.github">{{author.github}}</a></span>
        </div>
      </div>
    </div>
    <div class="topic-content">
      <div class="content" v-for="(content, index) in contents" :key="'content-' + index">
        <i :class="getContentClass(content.type)"></i>
        <div class="content-info">
          <h3><a target="_blank" :href="content.link">{{content.title}}</a></h3>
          <div class="sub-links">
            <span class="author"><i :class="'devicon-' + content.topic + '-plain colored'"></i><a :href="'/konu/' + content.topicId">{{content.topicName}}</a></span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Yazar',
  components: { },
  layout: 'page',
  data() {
    return {
      contents_local: [
        { topicTitle: "Android", topic:"android", type: "www", author: "Mobilhanem", title: "Mobilhanem", link: "https://www.mobilhanem.com" },
        { topicTitle: "Android", topic:"android", type: "www", author: "Yusuf Çakal", title: 'Android Günlüğü', link: "http://yusufcakal.com" },
        { topicTitle: "Android", topic:"android", type: "medium", author: "Yusuf Çakal", title: 'Android Uygulamaya "Facebook ile Giriş" Ekleme', link: "https://medium.com/@yusufcakal/android-uygulamaya-facebook-ile-giri%C5%9F-ekleme-14940166eb22" },
        { topicTitle: "Angular", topic:"angularjs", type: "www", author: "Ümit Köse", title: 'umiitkose.com Android Blog', link: "http://www.umiitkose.com/android" },
        { topicTitle: "VueJS", topic:"vuejs", type: "pdf", author: "Ümit Köse", title: 'Android Türkçe PDF', link: "http://umiitkose.com/wp-content/uploads/2015/08/AndroidStudio.pdf" },
        { topicTitle: "React", topic:"react", type: "youtube", author: "Levent Yadırga", title: 'Android Studio ile Uygulama Geliştirme Eğitimi', link: "https://www.youtube.com/playlist?list=PL9qDMO9EzLX25NTHm0q7svKLx__OZY8-e" },
        { topicTitle: "JavaScript", topic:"javascript", type: "medium", author: "Halil Özel", title: 'Android KTX Nedir ?', link: "https://medium.com/@halilozel1903/android-ktx-nedir-84ecbc615bfb" },
        { topicTitle: "CSS", topic:"css3", type: "medium", author: "Halil Özel", title: 'App Inventor Nedir ?', link: "https://medium.com/@halilozel1903/app-inventor-nedir-c37215ae598a" },
      ],
      contents: null,
      author: {},
    }
  },
  async fetch() {
    this.author = await fetch('https://turkcekaynaklar-backend-d6rdc62m6q-ey.a.run.app/api/authors/' + this.$route.params.id)
    .then(response => response.json())
    .then(response => response[0])

    this.contents = await fetch('https://turkcekaynaklar-backend-d6rdc62m6q-ey.a.run.app/api/authors/' + this.$route.params.id +'/resources')
    .then(response => response.json())
  },
  methods: {
    getContentClass(type) {
      if(type === "www") return "fab fa-chrome";
      else if(type === "youtube") return "fab fa-youtube";
      else if(type === "medium") return "fab fa-medium";
      else if(type === "pdf") return "fas fa-file-pdf"
    },
    getClassFromLink(profile) {
      
    },
    getProfileName(profile) { }
  }
}

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

    img.profile-pic {
      width: 4rem;
      height: 4rem;
      display: block;
      margin-right: 1rem;
      text-align: left;
    }

    .topic-info {
      display: flex;
      flex-direction: column;
      justify-content: space-between;

      h1 {
        font-weight: 400; margin-bottom: .625rem;
        line-height: 100%;
      }

      p { font-size: 1rem; margin-bottom: .75rem; }

      span.profile-link {
        color: var(--c-text-secondary);
        margin-right: 2.5rem;

        &::before {
          font-size: .875rem;
          margin-right: .25rem;
        }

        &.twitter::before {
          font-family: "Font Awesome 5 Brands"; content: "\f099";
        }

        &.instagram::before {
          font-family: "Font Awesome 5 Brands"; content: "\f16d";
        }

        &.youtube::before {
          font-family: "Font Awesome 5 Brands"; content: "\f167";
        }

        &.linkedin::before {
          font-family: "Font Awesome 5 Brands"; content: "\f08c";
        }

        &.github::before {
          font-family: "Font Awesome 5 Brands"; content: "\f09b";
        }

        &.website::before {
          font-family: "Font Awesome 5 Free"; content: "\f0c1"; font-weight: 900;
        }

        a {
          color: var(--c-text-secondary);
          text-decoration: none;

          &:hover {
            text-decoration: underline;
          }
        }
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
        justify-items: flex-start;

        h3 {
          font-weight: 400;
          margin-bottom: .5rem;

          a { color: var(--c-ontheme); }
        }

        span.author {
          font-size: .875rem;
          color: var(--c-border-dark);
          display: flex;
          flex-direction: row;
          align-items: center;
          justify-items: center;
          
          &:nth-child(2) {
            margin:0 .5rem;
          }

          a { color: var(--c-text-secondary); }

          i {
            width: auto;
            font-size: .875rem;
            margin-right: .25rem;
          }
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
