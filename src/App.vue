<template>
  <div id="app">
    <a-scene style="position: absolute; height: 100%; width: 100%;">
    <a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9"></a-box>
    <a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E"></a-sphere>
    <a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="#FFC65D"></a-cylinder>
    <a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="#7BC8A4"></a-plane>
    <a-sky color="#ECECEC"></a-sky>
      <a-entity id="leftHand" hand-tracking-controls="hand: left;"></a-entity>
      <a-entity id="rightHand" hand-tracking-controls="hand: right;"></a-entity>

      <a-text
          value="SSYARCH"
          position="-2 1.5 -3"
          rotation="0 0 0"
          color="#000000"
          align="center"
          geometry="primitive:plane"
          width="24">
      </a-text>
    </a-scene>
<div style="position: absolute; width: 30%; left:30%; top:30%; margin:auto">
  {{ name }}
</div>
    <div style="position: absolute; width: 30%; left:30%; top:40%; margin:auto">
      {{ calculation }}
    </div>
    <input           @keydown="calculateSpeed" style="position: absolute; width: 30%; left:30%; top:50%; margin:auto" v-model="name" />
  </div>
</template>

<script>
import 'aframe'; // Import A-Frame

export default {
  name: 'App',
  data() {
    return {
      name: '',
      calculation:'',
      lastKeyDownTime: 0,
      lastKeyUpTime:0,
      typingSpeeds: []
    };
  },
  methods: {
    setName(event) {
      console.log(event.detail.value); // Handle the name input
    },

    recordStartTime(event) {
      // Record the current time on keydown
      this.lastKeyDownTime = event.timeStamp;
    },
    calculateSpeed(event) {
      let time = event.timeStamp
      // Calculate the speed based on the time difference between keydown and keyup
      let speed = time - this.lastKeyUpTime;
      this.lastKeyUpTime = time;

      this.calculation = this.calculation.concat(String(speed)).concat("-")
    }

  }
}
</script>

<style>
/* Add any styles you need */
</style>
