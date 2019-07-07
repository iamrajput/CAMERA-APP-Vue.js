<template>
  <div class="camera">
    <video autoplay class="feed"></video>
    <button class="snap" v-on:click="$emit('takePicture')">SNAP</button>
  </div>
</template>

<script>
export default {
  name: "camera",
  methods: {
    init() {
      if (
        "mediaDevices" in navigator &&
        "getUserMedia" in navigator.mediaDevices
      ) {
        let constraints = {
          video: {
            width: { min: 600, max: 800 },
            height: { min: 360, max: 800 }
          }
        };

        navigator.mediaDevices.getUserMedia(constraints).then(stream => {
          const videoPlayer = document.querySelector("video");
          videoPlayer.srcObject = stream;
          videoPlayer.play();
        });
      }
    }
  },
  beforeMount() {
    this.init();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.camera {
  width: 100vw;
  height: 100vh;
  padding: 25px;
  box-sizing: border-box;
}
.feed {
  display: block;
  width: 100%;
  max-width: 700px;
  box-shadow: 6px 6px 12px 0px rgba(0, 0, 0, 0.35);
  margin: 0 auto;
  background-color: #171717;
  border-radius: 25px;
}
.snap {
  width: 75px;
  height: 75px;
  border-radius: 50%;
  display: block;
  background-color: transparentize($color: #ffce00, $amount: 0.75);
  border: 1px solid #171717;
  outline: none;
  margin: 25px auto;
  cursor: pointer;
  &:hover {
    background-color: crimson;
  }
  &:active {
    background-color: darken($color: #ffce00, $amount: 15);
  }
}
</style>
