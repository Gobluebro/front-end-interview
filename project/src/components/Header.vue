<template>
  <header class="bg-gray-500 text-white text-2xl flex">
    <img
      src="../assets/images/miranda-anderson/profile-image.jpg"
      alt="A Photo of Miranda Anderson"
    />
    <div class="flex-col">
      <span>{{ firstName }} {{lastName}}</span>
      <span>{{ blogName }}</span>
    </div>
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
</style>
