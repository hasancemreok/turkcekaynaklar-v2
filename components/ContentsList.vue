<template>
  <div class="x-container">
    <div class="topic" v-for="(topic, index) in topics" :key="'topic-' + index">
      <router-link :to="'/konu/' + topic.name">
        <!--<img :src="require('../static/topics/android.png')" :alt="topic.title">-->
        <i :class="topic.class"></i>
        <h2>{{topic.title}}</h2>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ContentsList',
  props: { },
  data() {
    return {
      topics: [
        { class:"devicon-android-plain colored", name: "android", title: "Android" },
        { class:"devicon-angularjs-plain colored", name: "angular", title: "Angular" },
        { class:"devicon-dot-net-plain colored", name: "aspnet", title: "ASP.NET" },
        { class:"fas fa-codex", name: "arduino", title: "Arduino" },
        { class:"fas fa-codex", name: "bash", title: "Bash" },
        { class:"fas fa-codex", name: "blockchain", title: "Blockchain" },
        { class:"fas fa-codex", name: "bot-framework", title: "Bot Framework" },
        { class:"fas fa-codex", name: "behavior-driven-development", title: "Behavior Drivent Development" },
        { class:"devicon-c-plain colored", name: "c", title: "C" },
        { class:"devicon-csharp-plain colored", name: "csharp", title: "C#" },
        { class:"devicon-clojure-plain colored", name: "clojure", title: "Clojure" },
        { class:"devicon-codeigniter-plain colored", name: "code-igniter", title: "CodeIgniter" },
        { class:"devicon-cplusplus-plain colored", name: "cpp", title: "C++" },
        { class:"fas fa-codex", name: "crystal", title: "Crystal" },
        { class:"devicon-css3-plain colored", name: "css", title: "CSS" },
        { class:"fas fa-codex", name: "d", title: "D" },
        { class:"fas fa-codex", name: "dart", title: "Dart" },
        { class:"fas fa-codex", name: "deep-learning", title: "Deep Learning" },
        { class:"devicon-django-plain colored", name: "django", title: "Django" },
        { class:"devicon-docker-plain colored", name: "docker", title: "Docker" },
        { class:"devicon-electron-original colored", name: "electron", title: "Electron" },
        { class:"fas fa-codex", name: "flux", title: "Flux" },
        { class:"devicon-flutter-plain colored", name: "flutter", title: "Flutter" },
        { class:"devicon-git-plain colored", name: "git", title: "Git" },
        { class:"devicon-linux-plain colored", name: "gnu-linux", title: "GNU/Linux" },
        { class:"devicon-go-plain colored", name: "golang", title: "Go" },
        { class:"fas fa-codex", name: "graphql", title: "GraphQL" },
        { class:"devicon-gulp-plain colored", name: "gulp", title: "Gulp" },
        { class:"devicon-haskell-plain colored", name: "haskell", title: "Haskell" },
        { class:"devicon-html5-plain colored", name: "html", title: "HTML" },
        { class:"devicon-ionic-original colored", name: "ionic", title: "Ionic" },
        { class:"devicon-java-plain colored", name: "java", title: "Java" },
        { class:"devicon-javascript-plain colored", name: "javascript", title: "JavaScript" },
        { class:"devicon-jquery-plain colored", name: "jquery", title: "jQuery" },
        { class:"devicon-kotlin-plain colored", name: "kotlin", title: "Kotlin" },
        { class:"devicon-laravel-plain colored", name: "laravel", title: "Laravel" },
        { class:"fas fa-codex", name: "machine-learning", title: "Machine Learning" },
        { class:"fas fa-codex", name: "matlab", title: "Matlab" },
        { class:"devicon-mongodb-plain colored", name: "mongodb", title: "MongoDB" },
        { class:"devicon-nginx-plain colored", name: "nginx", title: "Nginx" },
        { class:"devicon-nodejs-plain colored", name: "nodejs", title: "NodeJS" },
        { class:"fas fa-codex", name: "openssl", title: "OpenSSL" },
        { class:"fas fa-codex", name: "osx", title: "OSX" },
        { class:"fas fa-codex", name: "packer", title: "Packer" },
        { class:"devicon-php-plain colored", name: "php", title: "PHP" },
        { class:"devicon-python-plain colored", name: "python", title: "Python" },
        { class:"devicon-react-plain colored", name: "react", title: "React" },
        { class:"devicon-react-plain colored", name: "react-native", title: "React Native" },
        { class:"devicon-ruby-plain colored", name: "ruby", title: "Ruby" },
        { class:"devicon-ruby-plain colored", name: "ruby-on-rails", title: "Ruby on Rails" },
        { class:"fas fa-codex", name: "sketch", title: "Sketch" },
        { class:"fas fa-codex", name: "solidty", title: "Solidty" },
        { class:"fas fa-codex", name: "sql", title: "SQL" },
        { class:"devicon-swift-plain colored", name: "swift", title: "Swift" },
        { class:"fas fa-codex", name: "titanium-mobile", title: "Titanium Mobile" },
        { class:"fas fa-codex", name: "unit-testing", title: "Unit Testing" },
        { class:"fas fa-codex", name: "vault", title: "Vault" },
        { class:"devicon-vim-plain colored", name: "vim", title: "Vim" },
        { class:"devicon-vuejs-plain colored", name: "vue", title: "VueJS" },
        { class:"devicon-wordpress-plain colored", name: "wordpress", title: "Wordpress" },
        { class:"fas fa-codex", name: "xamarin", title: "Xamarin" },
        { class:"fas fa-link", name: "diger-kaynaklar", title: "Faydalı Linkler" },
        { class:"fab fa-youtube", name: "youtube-kanallari", title: "Youtube Kanalları" },
        { class:"fas fa-podcast", name: "podcast-yayinlari", title: "Podcast Yayınları" },
        { class:"devicon-slack-plain colored", name: "slack-gruplari", title: "Slack Grupları" },
      ]
    }
  }
}

</script>

<style lang="scss" scoped>
  .x-container {
    padding-top: .5rem;
    display: flex;
    flex-direction: column;
  }

  .topic {
    width: 100%;
    clear: both;

    a {
      width: 100%;
      display: flex;
      flex-direction: row;
      align-items: center;
      padding: 1rem .5rem;
      text-decoration: none;
      border-bottom: 1px solid #F0F0F0;
      transition: all .075s;

      img {
        width: 1.5rem;
        margin-right: 1rem;
      }

      i {
        width: 3rem;
        height: auto;
        margin-right: 1rem;
        font-size: 1.75rem;
        text-align: left;

        &.fa-codex { color: #969696; }
        &.fa-youtube { color: red; }
        &.fa-podcast { color: blueviolet; }
      }

      h2 {
        color: #02030F;
        font-weight: 400;
      }

      &:hover {
        background-color: #F7F7F7;
        padding-left: .5rem;
      }
    }
  }


</style>