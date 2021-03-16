<template>
  <div id="app">
    <Menu/>
  </div>
</template>

<script>
import Menu from './components/Menu.vue'

export default {
  name: 'App',
  components: {
    Menu
  }
}
</script>

<style>

/* ALL */
  * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
  }

  html {
      width: 100%;
      height: 100%;
  }

  body{
      background-image: url("assets/fond.jpg");
      background-repeat: no-repeat;
      background-size: cover;
  }

  #app {
      font-family: Avenir, Helvetica, Arial, sans-serif;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      text-align: center;
      color: #2c3e50;
      margin-top: 60px;
  }

</style>
