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
    --color1: #F6F4F3;
    --color2: #1b998ace;
    --color3: #276FBF;
    --color4: #183059;
    --color5: #a62b2b;
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