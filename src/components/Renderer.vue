<template>
  <div id="renderer"></div>
</template>

<script>
import * as PIXI from "pixi.js";

const WIDTH = 800;
const HEIGHT = 600;
const GRIDX = 120;
const GRIDY = 100;

const UNITDIMENSION =
  WIDTH / GRIDX < HEIGHT / GRIDY
    ? Math.floor(WIDTH / GRIDX)
    : Math.floor(HEIGHT / GRIDY);

const app = new PIXI.Application();

export default {
  props: {
    data: Array,
    color: Array,
  },
  mounted: function () {
    document.getElementById("renderer").appendChild(app.view);

    for (let x = 0; x < this.color[0].length; x++) {
      for (let y = 0; y < this.color.length; y++) {
        app.stage.addChild(
          new PIXI.Graphics()
            .beginFill(this.color[y][x])
            .drawRect(
              x * UNITDIMENSION,
              y * UNITDIMENSION,
              UNITDIMENSION,
              UNITDIMENSION
            )
        );
      }
    }
  },
};
</script>

<style>
</style>