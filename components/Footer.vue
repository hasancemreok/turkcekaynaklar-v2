<template>
  <div class="f-container">
    <div class="x-container">
      <a class="mr-1rem" href="https://turkcekaynaklar.com">Türkçe Kaynaklar</a>&bull;<a class="mr-1rem ml-1rem" target="_blank" href="https://twitter.com/fatihacet">Fatih Acet</a>
      <!--<a href="https://turkcekaynaklar.com">Github</a>&nbsp;ya da&nbsp;<a href="https://twitter.com/fatihacet">GitLab</a>'da katkıda bulunun.-->
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .f-container {
    margin-top: 2rem;
    border-top: 1px solid var(--c-theme-mid);
    height: 12rem;
    padding: 2rem;
    background-color: var(--c-theme);

    .x-container {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: row;
      text-align: center;
      line-height: 1.25rem;
      color: var(--c-border-light); 

      a { 
        text-decoration: none;
        color: var(--c-text-secondary); 
        
        &:hover {
          text-decoration: underline;
        }
      }
    }
  }

  .mr-1rem {
    margin-right: 1rem;
  }

  .ml-1rem {
    margin-left: 1rem;
  }
</style>