<template>
  <canvas ref="canvas" class="absolute top-0 left-0 w-full h-full z-0"></canvas>
</template>

<script setup>
import { onMounted, onBeforeUnmount, ref } from "vue";

const canvas = ref(null);
const speed = 0.2 // lower = slower
let ctx, width, height, columns, drops, animationId;
let speeds = [];

function initCanvas() {
  width = window.innerWidth;
  height = window.innerHeight;
  canvas.value.width = width;
  canvas.value.height = height;

  ctx = canvas.value.getContext("2d");
  const fontSize = 14;
  columns = Math.floor(width / fontSize);
  drops = Array(columns).fill(1);
}

function draw() {
  ctx.fillStyle = "rgba(0, 0, 0, 0.08)"; // fade trail
  ctx.fillRect(0, 0, width, height);

  ctx.fillStyle = "#8b5cf6"; // your purple rain
  ctx.font = "14px monospace";

  drops.forEach((y, i) => {
    const text = String.fromCharCode(0x30A0 + Math.random() * 96);
    const x = i * 14;
    ctx.fillText(text, x, y * 14);

    if (y * 14 > height && Math.random() > 0.99) {
      drops[i] = 0;
    }

    if (Math.random() > 0.75) {
        drops[i]++;
    }
  });

  animationId = requestAnimationFrame(draw);
}

onMounted(() => {
  initCanvas();
  draw();
  window.addEventListener("resize", initCanvas);
});

onBeforeUnmount(() => {
  cancelAnimationFrame(animationId);
  window.removeEventListener("resize", initCanvas);
});
</script>
