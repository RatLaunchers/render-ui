<template>
  <div id="renderer"></div>
</template>

<script>
import * as PIXI from "pixi.js";

const WIDTH = 820;
const HEIGHT = 620;
const GRIDX = 133;
const GRIDY = 100;

const UNITDIMENSION =
  WIDTH / GRIDX < HEIGHT / GRIDY
    ? Math.floor(WIDTH / GRIDX)
    : Math.floor(HEIGHT / GRIDY);

const app = new PIXI.Application({
  width: WIDTH,
  height: HEIGHT,
  backgroundAlpha: 0,
});

let gridObjects = [];
const grid = new PIXI.Container();

// Grid units init

for (let y = 0; y < GRIDY; y++) {
  gridObjects.push([]);
  for (let x = 0; x < GRIDX; x++) {
    gridObjects[y].push(new PIXI.Graphics());
    gridObjects[y][x].lineStyle(1, 0x000000, 1, 0.5);
    gridObjects[y][x].drawRect(
      x * UNITDIMENSION,
      y * UNITDIMENSION,
      UNITDIMENSION,
      UNITDIMENSION
    );
    grid.addChild(gridObjects[y][x]);
  }
}

//temp
const texture = PIXI.Texture.from("/map1.png");
const image = new PIXI.Sprite(texture);

image.anchor.x = 0;
image.anchor.y = 0;
image.position.x = 0;
image.position.y = 0;
image.width = UNITDIMENSION * GRIDX;
image.height = UNITDIMENSION * GRIDY;

export default {
  props: {
    data: Array,
    color: Array,
    images: Array,
  },
  methods: {
    test: function () {
      console.log("tset");
      gridObjects[5][5]
        .clear()
        .beginFill(Math.floor(Math.random() * 16777215), 1)
        .lineStyle(1, 0x000000, 1, 0.5)
        .drawRect(
          5 * UNITDIMENSION,
          5 * UNITDIMENSION,
          UNITDIMENSION,
          UNITDIMENSION
        );
      app.renderer.render(grid);
    },
    setGridColor: function (x, y, color) {
      console.log("tset");
      gridObjects[x][y]
        .clear()
        .beginFill(color, 1)
        .lineStyle(1, 0x000000, 1, 0.5)
        .drawRect(
          x * UNITDIMENSION,
          y * UNITDIMENSION,
          UNITDIMENSION,
          UNITDIMENSION
        );
      app.renderer.render(grid);
    },
  },
  mounted: function () {
    document.getElementById("renderer").appendChild(app.view);
    app.stage.addChild(image);
    app.stage.addChild(grid);
    app.ticker.add(() => {
      app.renderer.render(image, grid);
    });

    // for (let x = 0; x < this.color[0].length; x++) {
    //   for (let y = 0; y < this.color.length; y++) {
    //     app.stage.addChild(
    //       new PIXI.Graphics()
    //         .beginFill(this.color[y][x]/*[0] * (2000)*/)
    //         .drawRect(
    //           x * UNITDIMENSION,
    //           y * UNITDIMENSION,
    //           UNITDIMENSION,
    //           UNITDIMENSION
    //         )
    //     );
    //   }
    // }
  },
};
</script>

<style>
</style>