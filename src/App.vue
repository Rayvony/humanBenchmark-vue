<template>
<h1> Human Benchmark</h1>
<button @click="start" :disabled="isPlaying">Start new game</button>
<BlockTarget v-if="isPlaying" :delay="delay" />
</template>

<script setup>
import BlockTarget from './components/BlockTarget.vue';
import { ref } from 'vue';

const isPlaying = ref(false);
const delay = ref(null);

function start() {
  delay.value = 2000 + Math.random() * 5000;
  isPlaying.value = true;
}


</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  margin-top: 60px;
}
</style>
