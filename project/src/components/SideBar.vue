<template>
  <aside class="flex flex-col">
    <span class="flex flex-row">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 20 20"
        fill="currentColor"
        width="24px"
        height="24px"
        class="text-white"
      >
        <path
          fill-rule="evenodd"
          d="M5.05 4.05a7 7 0 119.9 9.9L10 18.9l-4.95-4.95a7 7 0 010-9.9zM10 11a2 2 0 100-4 2 2 0 000 4z"
          clip-rule="evenodd"
        />
      </svg>
      <span class="text-gray-400">
        {{ location }}
      </span>
    </span>
    <span class="text-gray-400">{{ sideBarData["email"] }}</span>
    <a v-bind:href="sideBarData['blog-url']"
      ><span class="text-white">{{ shortenedURL }}</span></a
    >
    <SocialIcon :accounts="sideBarData['social-media-accounts']"></SocialIcon>
    <hr />
    <span class="text-gray-400">FOCUS</span>
    <span class="text-white">{{ formattedFocusData }}</span>
    <span class="text-gray-400">RETAILERS FREQUENTED</span>
    <span class="text-white">{{ formattedRetailers }}</span>
    <span class="text-gray-400">PERSONAL DETAILS</span>
    <span class="text-white">{{ relationship }}</span>
    <span class="text-white">{{ numKids }}</span>
    <span class="text-white">{{ gender }}</span>
  </aside>
</template>

<script>
import SocialIcon from "./SocialIcon.vue";

export default {
  props: ["sideBarData"],
  components: {
    SocialIcon,
  },
  data: function() {
    return {
      location:
        this.sideBarData["city"].toUpperCase() +
        ", " +
        this.sideBarData["state"].toUpperCase(),
      shortenedURL: this.ShortenURL(this.sideBarData["blog-url"]),
      formattedFocusData: this.ChoicesFormat(
        this.sideBarData["content-topics"]
      ),
      formattedRetailers: this.ChoicesFormat(
        this.sideBarData["retailers-frequented"]
      ),
      relationship: this.GetRelationshipStatus(),
      numKids: this.GetNumOfKids(),
      gender: this.GetGender(),
    };
  },
  methods: {
    ShortenURL: function(url) {
      const urlWithoutProtocol = new URL(url).host;
      return urlWithoutProtocol;
    },
    ChoicesFormat: function(choices) {
      let addSpaces = choices.replaceAll("_", " ");
      let completedFormat = addSpaces.replaceAll(",", ", ");
      return completedFormat;
    },
    GetRelationshipStatus: function() {
      let gender = "";

      if (this.sideBarData["married"]) {
        gender += "MARRIED";
      } else {
        gender += "SINGLE";
      }

      return gender;
    },
    GetNumOfKids: function(){
      let numberOfKids = ""; 
      if (this.sideBarData["number-of-kids"] > 0) {
        numberOfKids += this.sideBarData["number-of-kids"];
        if (this.sideBarData["number-of-kids"] === 1){
          numberOfKids += " KID";
        }
        else {
          numberOfKids += " KIDS";
        }
      }
      return numberOfKids;
    },
    GetGender: function(){
      return this.sideBarData["gender"].toUpperCase();
    },
  },
};
</script>

<style scoped></style>
