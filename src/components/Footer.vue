<template>
  <div class="footer-area">
    <p>Made using <span><a href="https://vuejs.org/">Vue JS</a></span> by <span><a href="https://zonayed.me">Zonayed Ahmed</a></span></p>
  </div>
</template>

<script>
export default {
  name: 'Footer',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  a {
    display: inline-block;
    background: #41b883;
    color: #fff;
    text-decoration: none;
    padding: 2px 8px;
    text-transform: uppercase;
    font-weight: 900;
    border-radius: 4px;
  }

  p {
    font-size: 16px;
  }

  .footer-area {
    padding: 50px 0;
  }
</style>
