<template>
  <div class="f-container">
    <div class="x-container jumbotron">
      <img class="logo" src="~/static/logo.png" alt="turkcekaynaklar.com">
      <input type="text" placeholder="Türkçe kaynak arayın..." autocomplete="none" />
      <div class="buttons">
        <a href="#" class="btn btn-primary">
          <i class="fas fa-pen"></i>Sen de katkıda bulun</a>
        <a href="#" class="btn btn-normal">
          <i class="fab fa-github"></i>Github'da Görüntüle</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Jumbotron',
  props: {
    msg: String,
  },
};
</script>

<style scoped lang="scss">

  .f-container {
    background: url('../static/f-container-bg.png'), linear-gradient(to left bottom, rgb(179, 213, 255) 0%, rgb(231, 255, 179) 100%)
  }

  img.logo {
    width: 16rem;
    height: 9rem;
    border-color: antiquewhite;
    margin-bottom: 2rem;
    border-radius: .5rem;
  }

  .jumbotron {
    align-items: center;
    justify-content: center;
    align-content: space-around;
    flex-direction: column;
  }

  input[type="text"], .buttons {
    width: 64%;
    margin-bottom: 1rem;
  }

  .buttons {
    display: flex;
    flex-direction: row;
    align-content: space-around;
    align-items: center;
    justify-content: center;
    
    a {
      width: 50%;
      font-weight: 400;
      text-align: center;
      &:first-child { margin-right: 1rem; }
    }
  }

</style>
