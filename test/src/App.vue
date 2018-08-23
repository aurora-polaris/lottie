<template>
  <div id="app">
    <lottie :options="defaultOptions" :height="400" :width="400" v-on:animCreated="handleAnimation"/>
    <div>
      <p>Speed: x{{animationSpeed}}</p>
      <input
        type="range"
        value="1"
        min="0"
        max="3"
        step="0.5"
        v-on:change="onSpeedChange"
        v-model="animationSpeed">
    </div>
    <button @click="stop">stop</button>
    <button @click="pause">pause</button>
    <button @click="play">play</button>
  </div>
</template>

<script>
import Lottie from 'vue-lottie'
import * as animationData from './assets/pumped_up.json'

export default {
  name: 'app',
  components: {
    'lottie': Lottie
  },
  data () {
    return {
      defaultOptions: { animationData: animationData },
      animationSpeed: 1,
      anim: {}
    }
  },
  methods: {
    handleAnimation (anim) {
      this.anim = anim
      console.log(anim)
    },
    // 停止动画
    stop () {
      this.anim.stop()
    },
    // 开始动画
    play: function () {
      this.anim.play()
    },
    // 暂停动画
    pause: function () {
      this.anim.pause()
    },
    // 动画速度
    onSpeedChange () {
      this.anim.setSpeed(this.animationSpeed)
    }
  }
}
</script>
