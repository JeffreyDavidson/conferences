<template>
  <div id="app">
    <Navigation />
    <router-view class="container" :user="user" />
  </div>
</template>

<script>
import Navigation from "@/components/Navigation.vue";
import Firebase from "firebase";
import db from "./db.js";

export default {
  name: "app",
  data: function() {
    return {
      user: null
    }
  },
  components: {
    Navigation
  },
  mounted() {
    db.collection("users")
      .doc("4NzY9NE4j3TOtt2z8ar6")
      .get()
      .then(snapshot => {
        this.user = snapshot.data().name;
      });
  },
};
</script>

<style lang="scss">
$primary: #05b2dd;
@import "node_modules/bootstrap/scss/bootstrap"
</style>
