<template>
  <div class="f-container" :class="{'scrolled' : mode}" id="jumbotron">
    <div class="x-container jumbotron">
      <NuxtLink to="/" class="logo-link">
        <img class="logo" src="~/static/logo.png" alt="turkcekaynaklar.com">
      </NuxtLink>
      <input type="text" class="input-text" placeholder="Türkçe kaynak arayın..." autocomplete="none" />
      <div class="buttons">
        <a target="_blank " href="https://github.com/fatihacet/turkcekaynaklar-com/blob/master/Katki-Cagrisi.md" class="btn btn-primary" alt="Sen de katkıda bulun!">
          <i class="fas fa-pen"></i><span>Sen de katkıda bulun</span></a>
        <a target="_blank" href="https://github.com/fatihacet/turkcekaynaklar-com" class="btn btn-normal" alt="Github'da Görüntüle">
          <i class="fab fa-github"></i><span>Github'da Görüntüle</span></a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Jumbotron',
  props: {
    msg: String,
    mode: Boolean
  }
};
</script>

<style scoped lang="scss">

  .f-container {
    position: fixed;
    top: 0;
    border-bottom: 1px solid var(--c-border-dark);
    background: url('../static/f-container-bg.png'), linear-gradient(to left bottom, var(--c-jumbg-start) 0%, var(--c-jumbg-end) 100%);
    transition: all .15s;

    &.scrolled {
      height: 6rem;
      padding: 1rem 0;

      .jumbotron {
        flex-direction: row;
        justify-content: space-between;

        input.input-text {
          flex: 1;
          margin-right: 1rem;
        }

        input.input-text, .buttons {
          margin-bottom: 0;
        }

        a.logo-link {
          display: block;
          width: 4.75rem;
          height: 3rem;
          margin-bottom: 0;
          margin-right: 1rem;

          img.logo {
            width: 4.75rem;
            height: 3rem;
          }
        }

        .buttons {
          width: auto;

          a.btn { 
            i { margin-right: 0; }
            &:first-child { margin-right: 1rem; }

          }
          span { display: none; }
        }
      }
    }
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

  input.input-text, .buttons {
    width: 100%;
    margin-bottom: 1rem;
  }

  .buttons {
    display: flex;
    flex-direction: row;
    align-content: space-around;
    align-items: center;
    justify-content: center;
    
    a.btn {
      width: 50%;
      font-weight: 400;
      text-align: center;
      &:first-child { margin-right: 1rem; }
    }
  }

  @media only screen and (max-width: 991px) {

    .f-container {
      input.input-text {
        width: 100%;
      }

      .buttons {
        flex-direction: column;
        align-items: center;
        justify-content: center;

        a.btn {
          width: 100%;
          margin-right: 0;
          margin-bottom: .5rem;

          &:first-child { margin-right: 0;}
        }
      }

      &.scrolled {
        input.input-text {
          flex: 1;
        }

        .buttons {
          flex-direction: row;
          justify-items: center;
          align-content: space-between;

          a.btn {
            margin-bottom: 0;
          }
        }
      }
    }
  }

</style>
