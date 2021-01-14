<template>
  <div class="">
    <section id="photos">
      <img v-for="image in images" :key="image" v-bind:src="image" />
    </section>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      images: [],
      randomColors: [
        "bg-grey-600",
        "bg-red-600",
        "bg-green-600",
        "bg-blue-600",
        "bg-indigo-600",
        "bg-pink-600",
        "bg-purple-600",
      ],
    };
  },
  async mounted() {
    try {
      let imagesResponse = await axios.get(
        "https://dog.ceo/api/breeds/image/random/20"
      );
      if (imagesResponse.status == 200) {
        this.images = imagesResponse.data.message;
      }
    } catch (err) {
      console.log(err);
    }
  },
};
</script>

<!-- https://css-tricks.com/seamless-responsive-photo-grid/ -->
<!-- could also use masonry https://masonry.desandro.com/ -->
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#photos {
  /* Prevent vertical gaps */
  line-height: 0;

  -webkit-column-count: 4;
  -webkit-column-gap: 20px;
  -moz-column-count: 4;
  -moz-column-gap: 20px;
  column-count: 4;
  column-gap: 20px;
}

#photos img {
  width: 100% !important;
  height: auto !important;
  padding-bottom: 20px;
}

@media (max-width: 1200px) {
  #photos {
    -moz-column-count: 3;
    -webkit-column-count: 3;
    column-count: 3;
  }
}
@media (max-width: 1000px) {
  #photos {
    -moz-column-count: 2;
    -webkit-column-count: 2;
    column-count: 2;
  }
}
@media (max-width: 800px) {
  #photos {
    -moz-column-count: 1;
    -webkit-column-count: 1;
    column-count: 1;
  }
}
</style>
