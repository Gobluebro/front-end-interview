<template>
  <div class="">
    <img
      v-bind:src="IconSetter(socials.id)"
      v-bind:href="socials.link"
      v-bind:alt="socials.type"
    />
  </div>
</template>

<script>
export default {
  props: ["socials"],
  data: function() {
    return {
      src: "",
    };
  },
  methods: {
    IconSetter: function(id) {
      switch (id) {
        case 0:
          this.src = "../assets/icons/social-pinterest.svg";
          break;
        case 1:
          this.src = "../assets/icons/social-twitter.svg";
          break;
        case 2:
          this.src = "../assets/icons/social-instagram.svg";
          break;
        case 3:
          this.src = "../assets/icons/social-youtube.svg";
          break;
        default:
          break;
      }
    },
  },
};
</script>

<style scoped>
svg {
  fill: white;
}
</style>
