<template>
  <div id="app">
    <Cotacao />
  </div>
</template>

<script>
import Cotacao from "./components/Cotacao";

export default {
  name: "App",
  components: {
    Cotacao
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 20px;
}
</style>
