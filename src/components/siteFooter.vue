<template>
  <main>
    <footer class="flexWrap">
      <ul class="flexWrap">
        <li>&copy; Gui 2022</li>
        <li><a href="https://github.com/guic97">GitHub</a></li>
        <li><a href="https://www.linkedin.com/in/atila-guilherme-aa5638219/">LinkedIn</a></li>
      </ul>
    </footer>
  </main>
</template>

<script>
export default {
  name:'siteFooter',
}
</script>

<style scoped>
  footer{
    background-color: var(--color2);
    color: var(--color1);
    height: 100px;
    justify-content: center;
    align-items: center;
  }
  footer > ul >li{
    list-style-type: none;
    margin: 0 10px;
  }
  a{
    text-decoration: none;
    color: var(--color1);
  }
  a:hover{
    color: var(--color3);
  }
</style>