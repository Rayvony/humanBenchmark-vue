<template>
<h1> Human Benchmark</h1>
<button @click="start">Start new game</button>
</template>

<script setup>
import { ref } from 'vue';

const isPlaying = ref(false);
const delay = ref(null);

function start() {
  delay.value = 2000 + Math.random() * 5000;
  isPlaying.value = true;
  console.log('delay', delay.value);
}


</script>

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
