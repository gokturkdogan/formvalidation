<template>
  <div id="app">
    <formvalid/>
  </div>
</template>

<script>
import formvalid from "./components/form-valid.vue";

export default {
  name: 'App',
  components: {
    formvalid
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
 display: flex;
 justify-content: center;
 padding: 60px;
  margin-top: 60px;
  background-color: grey;
  width: 100%;
}
</style>
