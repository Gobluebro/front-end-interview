<template>
  <main class="text-white p-2">
    <span class="text-2xl">STORY COLLECTION</span>
    <br />
    <span class="text-gray-500 text-lg">All stores by {{ firstName }} {{ lastName }}</span>
    <ImageGrid></ImageGrid>
  </main>
</template>

<script>
import ImageGrid from "./ImageGrid.vue";

export default {
  props: ["firstName", "lastName"],
  components: {
    ImageGrid,
  },
  data: function() {
    return {
      images: [],
    };
  },
};
</script>

<style scoped></style>
