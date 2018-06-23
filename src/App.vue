<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <ContentArea/>
    <Footer />
  </div>
</template>

<script>
import ContentArea from './components/ContentArea'
import Footer from './components/Footer'

export default {
  name: 'App',
  data: function() {
    return {
      msg: 'To Do With Vue JS'
    }
  },
  components: {
    ContentArea, Footer
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

img {
  height: 60px
}

h1 {
  text-transform: uppercase;
  font-weight: 900;
}
</style>
