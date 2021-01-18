<template>
  <main class="text-white p-2 pl-8">
    <span class="text-2xl tracking-widest inline-block mt-5">STORY COLLECTION</span>
    <br />
    <span class="text-gray-500 text-xl inline-block mt-3 mb-8">All stores by {{ firstName }} {{ lastName }}</span>
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
