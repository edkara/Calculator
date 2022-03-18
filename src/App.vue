<script>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Calculator from './components/Calculator.vue'
// import { ParticlesBg } from "particles-bg-vue"

export default {
  name: "App",
  components: {
    Calculator
  }
}

</script>

<template>
  <Calculator />
  <!-- <particles-bg type="custom" :config="config" :bg="true" /> -->
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
