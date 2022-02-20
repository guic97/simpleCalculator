<template>
  <main>
    <footer class="flexWrap">
      <ul class="flexWrap">
        <li>&copy; Gui 2022</li>
        <li>GitHub</li>
        <li>LinkedIn</li>
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
</style>