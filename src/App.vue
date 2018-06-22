<template>
  <div class="outerAnimationDiv" :class="{'closeAnimation': startClosing}">
    <div class="animationDiv" :class="{'closeAnimation': startClosing}" ref="animationDiv" style="background: #fff">
      <LoadingAnimation></LoadingAnimation>
    </div>
    <div class="animationDiv" :class="{'closeAnimation': startClosing}" ref="animationDiv" style="background: #000">
      <LoadingAnimation></LoadingAnimation>
    </div>
    <div v-for="color in colors" :key="color">
      <div class="animationDiv" :class="{'closeAnimation': startClosing}" ref="animationDiv" :style="{'background': color}">
        <LoadingAnimation></LoadingAnimation>
      </div>
    </div>
  </div>
</template>

<script>
import LoadingAnimation from '@/components/LoadingAnimation.vue'

export default {
  name: 'App',
  components: {
    LoadingAnimation
  },
  data () {
    return {
      startClosing: false,
      animationHeight: '150px',
      colors: [],
      tiles: 6
    }
  },
  mounted () {
    for (let i = 0; i < this.tiles; i += 1) {
      this.colors.push(`hsla(${360 / this.tiles * i}, 20%, 50%, 1)`)
    }
  }
}
</script>

<style>
body{
  margin: 0;
  background: #222;
  display: flex;
}

.animationDiv {
    position: relative;
    display: inline-block;
    float:left;
    margin: 20px;
    width: 250px;
    height: calc(250px / 1.14);
    padding: 50px;
    border-radius: 100px;
    -webkit-transition: height 0.5s, margin-top 0.5s; /* Safari */
    transition: height 0.5s, margin-top 0.5s;
    border: 15px solid #000;
    background: #000;
}

.outerAnimationDiv {
    -webkit-transition: height 0.5s; /* Safari */
    transition: height 0.5s;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
}

.closeAnimation {
    height: 0;
    margin-top: 0;
}

</style>
