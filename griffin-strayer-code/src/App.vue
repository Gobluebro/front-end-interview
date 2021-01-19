<template>
  <div>
    <Loading v-if="loading"></Loading>
    <div v-if="!loading" class="flex flex-col bg-gray-800">
      <Header
        :firstName="layoutData['first-name']"
        :lastName="layoutData['last-name']"
        :blogName="layoutData['blog-name']"
      >
      </Header>
      <div class="flex real-smol-side-and-content-combo lg:flex-row">
        <SideBar class="real-smol-sidebar lg:order-first lg:w-1/4" :sideBarData="layoutData"></SideBar>
        <Content
          class="real-smol-content lg:order-last lg:w-3/4"
          :firstName="layoutData['first-name']"
          :lastName="layoutData['last-name']"
        >
        </Content>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Content from "./components/Content.vue";
import SideBar from "./components/SideBar.vue";
import Loading from "./components/Loading.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    Header,
    Content,
    SideBar,
    Loading,
  },
  data: function() {
    return {
      layoutData: {},
      loading: true,
    };
  },
  async created() {
    try {
      let dataResponse = await axios.get(
        "https://ahalogy-fe-interview-server.herokuapp.com/influencers/8634"
      );
      if (dataResponse.status == 200) {
        this.layoutData = dataResponse.data.data;
        this.loading = false;
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
  color: #2c3e50;
  margin-top: 60px;
}

@media only screen 
  and (min-device-width: 320px) 
  and (max-device-width: 568px)
  and (-webkit-min-device-pixel-ratio: 2) {
    .real-smol-side-and-content-combo{
      flex-direction: column;
    }
    .real-smol-sidebar{
      width:100%;
      order: 9999;
    }
    .real-smol-content{
      width:100%;
      order: -9999;
    }
}
</style>
