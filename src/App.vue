<template>
  <div class="x-logo">
    <a
      class="github-fork-ribbon"
      target="_blank"
      href="https://github.com/rmlzy/x-logo"
      data-ribbon="Fork me on GitHub"
      title="Fork me on GitHub"
    >
      Fork me on GitHub
    </a>

    <img class="logo" src="./assets/logo.png" alt="XLogo" />
    <h2 class="description">A XVIDEOS Flavour Logo Generator</h2>
    <x-videos></x-videos>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import XVideos from "./generator/XVideos.vue";
import "normalize.css";
import "github-fork-ribbon-css/gh-fork-ribbon.css";

export default defineComponent({
  name: "App",
  components: {
    XVideos,
  },
});
</script>

<style lang="less">
body {
  font-family: Arial, Helvetica, sans-serif;
  background-color: #010101;
}

.x-logo {
  padding: 40px 0;
  text-align: center;

  .logo {
    height: 40px;
  }

  .description {
    color: #fefefe;
  }
}
</style>
