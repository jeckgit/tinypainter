<script setup lang="ts">
import { ref } from 'vue';

const CELL_SIZE = 15;

const windowHeight = ref(window.innerHeight);
const windowWidth = ref(window.innerWidth);

const vertivalNumSquares = Math.floor(windowHeight.value / CELL_SIZE);
const horizontalNumSquares = Math.floor(windowWidth.value / CELL_SIZE);

const getRandomHexColor = () => {
  // Generate random values for red, green, and blue components
  const red = Math.floor(Math.random() * 256);
  const green = Math.floor(Math.random() * 256);
  const blue = Math.floor(Math.random() * 256);

  // Convert the decimal values to hexadecimal and concatenate
  const hexColor = `#${(red).toString(16).padStart(2, '0')}${(green).toString(16).padStart(2, '0')}${(blue).toString(16).padStart(2, '0')}`;

  return hexColor;
}

</script>

<template>
  <div class="fixed">
    <p>height: {{ windowHeight }}</p>
    <p>width: {{ windowWidth }}</p>
    <p>num squares vert: {{ vertivalNumSquares }} </p>
    <p>num squares hor: {{ horizontalNumSquares }} </p>
  </div>
  <div class="absolute top-0 left-0">
    <div v-for="(vert, idx) in vertivalNumSquares" :key="`vert-${idx}`" class="vert flex">
      <div v-for="(hor, idx) in horizontalNumSquares" :key="`hor-${idx}`" class="hor cell"
        :style="{ height: CELL_SIZE + 'px', width: CELL_SIZE + 'px', backgroundColor: getRandomHexColor() }" />
    </div>
  </div>
</template>
<style lang="css">
.vert {
  display: flex;
  width: 100%;
}
.cell {}
</style>