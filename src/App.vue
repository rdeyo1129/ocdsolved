<template>
  <div class="canvas-container" ref="canvasContainer">
    OCD SOLVED
    <div class="inner-cont" ref="canvas"></div>
  </div>
</template>

<script>
import p5 from "p5";

export default {
  name: "Sketch",
  mounted() {
    this.sketch = new p5(this.draw, this.$refs.canvas);
  },
  destroyed() {
    this.sketch.remove();
  },
  methods: {
    draw(p) {
      const width = 600;
      const height = 300;
      const centerX = width / 2;
      const centerY = height / 2;
      const radiusX = 200;
      const radiusY = 100;
      const canvasWidth = width;
      const canvasHeight = height;
      let x = centerX - radiusX;
      let y = centerY;
      let speed = 2;
      let directionX = 1;
      let directionY = 1;

      p.setup = () => {
        p.createCanvas(canvasWidth, canvasHeight);
        p.noStroke();
      };

      p.draw = () => {
        // Set background color
        p.background(0);

        // Draw colored background in center
        p.fill(50, 100, 200);
        p.rect(200, 50, 220, 220);

        // Draw box
        p.fill(255, 215, 0);
        p.rect(x, y, 20, 20);

        // Update position
        x += speed * directionX;
        y += speed * directionY;

        // Check boundaries
        if (x >= centerX + radiusX || x <= centerX - radiusX) {
          directionX *= -1;
        }
        if (y >= centerY + radiusY || y <= centerY - radiusY) {
          directionY *= -1;
        }
      };
    },
  },
};
</script>

<style>
.canvas-container {
  width: 600px;
  height: 200px;
  padding: 0;
}
.inner-cont {
  position: absolute;
  width: 600px;
  height: 200px;
}

canvas {
  display: block;
}
</style>
