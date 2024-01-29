<template>
  <div id="app">
    <a-scene style="position: absolute; height: 100%; width: 100%;">
    <a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9"></a-box>
    <a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E"></a-sphere>
    <a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="#FFC65D"></a-cylinder>
    <a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="#7BC8A4"></a-plane>
    <a-sky color="#ECECEC"></a-sky>
      <!-- Camera -->
      <a-camera position="0 1.6 0"></a-camera>

      <!-- Hand tracking controllers -->
      <a-entity id="left-hand" oculus-touch-controls="hand: left" hand-controls="hand: left" visible="true"></a-entity>
      <a-entity id="right-hand" oculus-touch-controls="hand: right" hand-controls="hand: right" visible="true"></a-entity>

      <!-- Cubes -->
      <a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9" dynamic-body></a-box>
      <a-box position="1 0.5 -3" rotation="0 45 0" color="#EF2D5E" dynamic-body></a-box>

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
    <input style="position: absolute; width: 30%" v-model="useragent" />
  </div>
</template>

<script>
import 'aframe'; // Import A-Frame
import 'aframe-physics-system'; // If you plan to use physics
export default {
  name: 'App',
  methods: {
    setName(event) {
      console.log(event.detail.value); // Handle the name input
    }
  }
}
</script>

<style>
/* Add any styles you need */
</style>
