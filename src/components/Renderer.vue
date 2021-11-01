<template>
  <div id="renderer"></div>
</template>

<script>
import * as PIXI from "pixi.js";
const app = new PIXI.Application();

export default {
  props: {
    data: Array,
    color: Array,
  },
  mounted: function () {
    document.getElementById("renderer").appendChild(app.view);

    const square = new PIXI.Graphics();
    app.stage.addChild(square);
    square.beginFill(8576732);
    square.drawRect(50, 250, 100, 100);
  },
};
</script>

<style>
</style>