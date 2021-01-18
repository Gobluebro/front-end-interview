<template>
  <div class="flex">
    <img
      v-for="account in accounts"
      :key="account.id"
      v-bind:src="IconSetter(account.id)"
      v-bind:href="account.link"
      v-bind:alt="account.type"
      height="50px"
      width="50px"
      class="mx-1.5"
    />
  </div>
</template>

<script>
import pinterest from "../assets/icons/social-pinterest.svg";
import twitter from "../assets/icons/social-twitter.svg";
import instagram from "../assets/icons/social-instagram.svg";
import youtube from "../assets/icons/social-youtube.svg";


export default {
  props: ["accounts"],
  methods: {
    IconSetter: function(id) {
      switch (id) {
        case 0:
          return pinterest;
        case 1:
          return twitter;
        case 2:
          return instagram;
        case 3:
          return youtube;
        default:
          return "";
      }
    },
  },
};
</script>

<style scoped>
img {
  filter: invert(100%);
  width: 35px;
  height: 35px;
}
</style>
