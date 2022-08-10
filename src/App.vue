<template>
  <div>
    <header><site-header/></header>
    <main><calculator/></main>
    <footer><site-footer/></footer>
  </div> 
</template>

<script>
  import siteHeader from "./components/siteHeader.vue";
  import calculator from "./components/calculator.vue";
  import siteFooter from './components/siteFooter.vue';

  export default {  
  name:'App',
  components:{
    siteHeader,
    calculator,
    siteFooter,
  },
}
</script>

<style>
  :root{
    --standardFont: Arial, Helvetica, sans-serif;
    --color1: #ffffff;
    --color2: #47cebece;
    --color3: #4483ca;
    --color4: #3f6bb8;
    --color5: rgb(29, 29, 29);
  }
  *{
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
    font-family: var(--standardFont);
  }
  .flexWrap{
    display: flex;
    flex-wrap: wrap;
  }
  footer{
    box-shadow: 0px 5px 10px black;
  }
</style>