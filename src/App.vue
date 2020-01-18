<template lang="html">
  <div id="app">
    <canvas class="game-board" id="snake" width="600" height="500">
      Sorry this game is not supported by your browers.
    </canvas>
  </div>
</template>

<script>
export default {
  name: "app",

  methods: {
    roundedRect(ctx, x, y, width, height, radius) {
      ctx.beginPath();
      ctx.moveTo(x, y + radius);
      ctx.lineTo(x, y + height - radius);
      ctx.arcTo(x, y + height, x + radius, y + height, radius);
      ctx.lineTo(x + width - radius, y + height);
      ctx.arcTo(x + width, y + height, x + width, y + height - radius, radius);
      ctx.lineTo(x + width, y + radius);
      ctx.arcTo(x + width, y, x + width - radius, y, radius);
      ctx.lineTo(x + radius, y);
      ctx.arcTo(x, y, x, y + radius, radius);
      ctx.stroke();
    },

    draw() {
      const canvas = document.getElementById("snake");
      if (canvas.getContext) {
        const ctx = canvas.getContext("2d");

        ctx.fillStyle = "green";
        // (left, top, width, height)
        ctx.fillRect(100, 100, 100, 0.5);
      }
    }
  },

  mounted() {
    this.draw();
  }
};
</script>

<style lang="css" scoped>
.game-board {
  background-color: #f2f2e7;
}

canvas {
  border: 1px solid black;
}
</style>
