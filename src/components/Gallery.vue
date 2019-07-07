<template>
  <div class="picture">
    <canvas></canvas>
  </div>
</template>

<script>
export default {
  name: "Gallery"
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.picture {
  width: 100vw;
  height: 100vh;
  padding: 20px;
  box-sizing: border-box;
  canvas {
    display: block;
    width: 100%;
    max-width: 500px;
    margin: 0 auto;
    box-shadow: 4px 4px 12px 0px transparentize($color: #17171717, $amount: 0.5);
    border-radius: 25px;
  }
}
</style>
