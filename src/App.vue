<template>
  <div id="app">
    <Camera v-on:takePicture="this.takePicture"/>
    <Gallery/>
  </div>
</template>

<script>
import Camera from "./components/Camera";
import Gallery from "./components/Gallery";
import { win32 } from "path";
export default {
  name: "app",
  components: {
    Camera,
    Gallery
  },
  methods: {
    takePicture() {
      let ratio = (window.innerHeight = window.innerWidth ? 16 / 9 : 9 / 16);
      const picture = document.querySelector("canvas");
      picture.width = window.innerWidth < 800 ? window.innerWidth : 800;
      picture.height = window.innerWidth / ratio;
      const ctx = picture.getContext("2d");
      ctx.imageSmoothingEnabled = true;
      ctx.imageSmoothingQuality = "high";
      ctx.drawImage(
        document.querySelector("video"),
        0,
        0,
        picture.width,
        picture.height
      );
    }
  }
};
</script>



<style lang="scss">
body {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: seashell;
  overflow-x: hidden;

}
</style>
