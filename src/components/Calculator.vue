<script setup lang="ts">
import { ref } from "vue";
</script>

<template>
  <div class="calculator">
    <div class="display">232132</div>
    <div class="item">AC</div>
    <div class="item">+/-</div>
    <div class="item">%</div>
    <div class="item operations">/</div>
    <div class="item">7</div>
    <div class="item">8</div>
    <div class="item">9</div>
    <div class="item operations">X</div>
    <div class="item">4</div>
    <div class="item">5</div>
    <div class="item">6</div>
    <div class="item operations">-</div>
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item operations">+</div>
  </div>
</template>

<style scoped>
.calculator {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(5rem, auto);
  /* grid-column-gap:.1rem;
  grid-row-gap:.1rem; */
  font-size: 3rem;
  /* shadow  */
}
.display {
  grid-column: 1/5;
  background-color: aquamarine;
}
.item {
  position: relative;
  background-color: white;
  color: black;
  text-align: center;
  border: solid 1px blue;
}
/* .item::after {
  content: "";
  position: absolute;
  width: 1px;
  height: 100%;
  right: 0;
  top: 0;
  background-color: blue;
  z-index: 1;
}
.item::before {
  content: "";
  position: absolute;
  width: 100%;
  height: 1px;
  left: 0;
  bottom: 0;
  background-color: blue;
  z-index: 1;
} */

.operations {
  background-color: orange;
  color: white;
}
</style>