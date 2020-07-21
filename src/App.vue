<template>
  <div id="app">
    <AddTask />
  </div>
</template>

<script>
import AddTask from "./components/AddTask.vue";

export default {
  name: "App",
  components: {
    AddTask
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #85e278;
  margin-top: 20px;
}
</style>
