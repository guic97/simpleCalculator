<template>
    <div>
        <h2>Idade: {{numero}}</h2>
    </div>
</template>

<script>
  export default{
    name: 'lifeCycle',
    data(){
      return{
        numero: 'None'
      }
    },
    created(){
      setTimeout((e) => {
          this.numero='24'
      }, 1000)  
    },
    mounted(){
      setTimeout((e) => {
          this.numero='25'
      }, 2000)
    },
  }
</script>
