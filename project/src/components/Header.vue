<template>
  <header
    class="bg-gray-700 text-white text-xl flex justify-start items-center"
  >
    <img
      src="../assets/images/miranda-anderson/profile-image.jpg"
      alt="A Photo of {{ firstName }} {{ lastName }}"
      class="mx-8 my-4 rounded-full"
      width="100"
      height="100"
    />
    <div class="flex flex-col">
      <span class="text-gray-400 ">{{ firstName }} {{ lastName }}</span>
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
header {
  margin-top: -60px;
}
</style>
