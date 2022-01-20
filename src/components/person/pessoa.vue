<template>
  <div>
      <p><lifeCycle/></p>
      <h2><imagemJinx/></h2>
      <h3>This person: {{personName}}</h3>
      <h4><dadosPessoa/></h4>
      <h3><a :href="linkJinx" target="_blank">My clip</a></h3>
  </div>
</template>

<script>
  import dadosPessoa from "./dadosPessoa"
  import imagemJinx from "./inserirImg.vue"
  import lifeCycle from "./lifeCycle.vue";
  export default{
    nome: 'pessoa',
    
    components:{
        dadosPessoa,
        imagemJinx,
        lifeCycle,
    },
      data(){
        return{
          personName: 'Jinx',
          linkJinx: 'https://www.youtube.com/watch?v=0nlJuwO0GDs',
        }
      }
    }
</script>
