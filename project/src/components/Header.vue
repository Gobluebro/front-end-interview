<template>
  <header
    class="bg-gray-500 text-white text-xl flex justify-start items-center"
  >
    <img
      src="../assets/images/miranda-anderson/profile-image.jpg"
      alt="A Photo of {{ firstName }} {{ lastName }}"
      class="row-span-3 mx-8 my-4"
    />
    <div class="flex flex-col">
      <span class="text-gray-400 "
        >{{ firstName }} {{ lastName }}</span
      >
      <span class="">{{ blogName }}</span>
    </div>
  </header>
</template>

<script>
export default {
  props: ["firstName", "lastName", "blogName"],
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
