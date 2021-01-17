<template>
  <header
    class="bg-gray-500 text-white text-xl grid grid-rows-3 grid-flow-col gap-2 justify-start items-center"
  >
    <img
      src="../assets/images/miranda-anderson/profile-image.jpg"
      alt="A Photo of Miranda Anderson"
      class="row-span-3 mx-8 my-4"
    /> 
    <span class="col-span-2 text-gray-400">{{ firstName }} {{ lastName }}</span>
    <span class="row-span-2 font-light">{{ blogName }}</span>
  </header>
</template>

<script>
export default {
  props: ["firstName", "lastName", "blogName"],
  data: function() {
    return {
      images: [],
    };
  },
};
</script>

<style scoped>
img {
  border-radius: 50%;
  width: 100px;
  height: 100px;
}
header {
  margin-top: -60px;
}
</style>
