<template>
  <main>
    <nav class="flexWrap">
      <ul class="flexWrap">
        <li>Home</li>
        <li>About</li>
        <li>Suport</li>
      </ul>
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
    background-color: var(--color2);
    color: var(--color1);
  }
   nav{
    height: 50px;
    align-content: center;
    justify-content: flex-start;
    margin-left: 15px;
  }
  nav > ul{ 
    list-style-type: none;
  }
  ul li{
    margin: 0 10px;
    text-shadow: 0px 1px 10px black;
  }
</style>