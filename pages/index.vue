<template>
  <div>
    <Game
      :img-origin="game.imgOrigin"
      :img-map="game.imgMap"
      :pic-scale="game.picScale"
      :click-color.sync="game.clickColor"/>
    <div ref="testColorDiv" class="testColor"></div>
  </div>

</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      game: {
        imgOrigin: require('./imgs/img.png'),
        imgMap: require('./imgs/img2.png'),
        picScale: 1.3,
        clickColor: null
      }
    }
  },
  watch: {
    'game.clickColor'() {
      const clickColor = this.game.clickColor
      const color = clickColor ? `rgb(${clickColor[0]}, ${ clickColor[1] }, ${ clickColor[2] })` : '';
      this.$refs.testColorDiv.style.backgroundColor = color

    }
  }
}
</script>
<style lang="scss" scoped>
.testColor {
  position: fixed;
  right: 0;
  bottom: 0;
  z-index: 10;
  width: 100px;
  height: 100px;
  background-color: #f00;
}

</style>