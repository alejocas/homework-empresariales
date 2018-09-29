<template>
  <div id="app">
    <h1>Busca tu producto en el mercado de Alejo</h1>
    <Shop></Shop>
  </div>
</template>

<script>
import Shop from "./components/Shop.vue";

export default {
  name: "app",
  components: {
    Shop
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  background-color: #FFF159;
}
</style>
