<template>
  <main>
    <nav class="flexWrap">
      <h1>Calculadora</h1>
    </nav>
  </main>  
</template>

<script>
export default {
  name:'siteHeader',
}
</script>

<style scoped>
  main{
    background-color: var(--color3);
  }
  nav{
    height: 60px;
    align-items: center;
    justify-content: center;
  }
  nav > h1{
    font-size: 30px;
    font-weight: bolder;
    text-shadow: 1px 1px 1px var(--color5);
    color: var(--color1);
  }
</style>