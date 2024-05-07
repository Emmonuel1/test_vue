<template>
  <div id="app">
    <itemsList />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import itemsList from "./components/itemsList.vue";

export default defineComponent({
  name: "App",
  components: {
    itemsList,
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>