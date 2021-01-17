<template>
  <div>
    <Header 
    :firstName="layoutData['first-name']" 
    :lastName="layoutData['last-name']"  
    :blogName="layoutData['blog-name']" 
    >
    </Header>
    <SideBar sideBarData="layoutData"></SideBar>
    <Content 
    :firstName="layoutData['first-name']" 
    :lastName="layoutData['last-name']" 
    >
    </Content>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Content from "./components/Content.vue";
import SideBar from "./components/SideBar.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    Header,
    Content,
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
        console.log(dataResponse.data.data);
        this.layoutData = dataResponse.data.data;
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
</style>
