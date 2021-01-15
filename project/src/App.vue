<template>
  <div>
    <SideBar sideBarData="layoutData"></SideBar>
    <ImageGrid></ImageGrid>
  </div>
</template>

<script>
import ImageGrid from "./components/ImageGrid.vue";
import SideBar from "./components/SideBar.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    ImageGrid,
    SideBar,
  },
  data: function() {
    return {
      layoutData: {},
    };
  },
  async mounted() {
    try {
      let dataResponse = await axios.get(
        "https://ahalogy-fe-interview-server.herokuapp.com/influencers/8634"
      );
      if (dataResponse.status == 200) {
        this.layoutData = dataResponse.data;
      }
    } catch (err) {
      console.log(err);
    }
  },
};
</script>

<style>
@font-face {
  font-family: "PT_Sans";
  src: url("./assets/fonts/PTSans-Regular.ttf") format("truetype");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "PT_Sans";
  src: url("./assets/fonts/PTSans-Italic.ttf") format("truetype");
  font-weight: normal;
  font-style: italic;
}

@font-face {
  font-family: "PT_Sans";
  src: url("./assets/fonts/PTSans-Bold.ttf") format("truetype");
  font-weight: bold;
  font-style: normal;
}

@font-face {
  font-family: "PT_Sans";
  src: url("./assets/fonts/PTSans-BoldItalic.ttf") format("truetype");
  font-weight: bold;
  font-style: italic;
}

#app {
  font-family: "PT_Sans", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
