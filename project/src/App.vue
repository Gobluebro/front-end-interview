<template>
  <div>
    <ImageGrid></ImageGrid>
  </div>
</template>

<script>
import ImageGrid from "./components/ImageGrid.vue";

export default {
  name: "App",
  components: {
    ImageGrid,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
