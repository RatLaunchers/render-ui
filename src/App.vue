<template>
  <div>
    <renderer :color="data.sample.colorBase"></renderer>
    <div>
      <data-input v-model="fireLocation.x" name="Fire location x"></data-input>
      <data-input v-model="fireLocation.y" name="Fire location y"></data-input>
      <data-input v-model="wind.velocity" name="Wind velocity"></data-input>
      <data-input v-model="wind.angle" name="Wind angle"></data-input>
      <data-input
        v-model="simulationSpeed"
        name="Simulation speed"
      ></data-input>
    </div>
  </div>
</template>

<script>
import DataInput from "./components/DataInput.vue";
import Renderer from "./components/Renderer.vue";
import * as data from "./data.js";

export default {
  data() {
    return {
      fireLocation: { x: 0, y: 0 },
      wind: { velocity: 0, angle: 0 },
      simulationSpeed: 1,
      data,
    };
  },
  components: {
    DataInput,
    Renderer,
  },
};
</script>

<style>
</style>
