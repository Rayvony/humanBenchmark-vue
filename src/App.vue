<template>
  <div class="target" @mousedown="tooSoon">
<h1> Human Benchmark</h1>
<button @click="start" :disabled="isPlaying">Start a new game</button>
<BlockTarget v-if="isPlaying" :delay="delay" :onEnd="handleEnd"/>
<ResultsBox v-if="score" :score="score"/>
  </div>
</template>

<script setup>
import BlockTarget from './components/BlockTarget.vue';
import ResultsBox from './components/ResultsBox.vue';
import { ref } from 'vue';

const isPlaying = ref(false);
const delay = ref(null);
const score = ref(null);

function start() {
  delay.value = 2000 + Math.random() * 5000;
  isPlaying.value = true;
  score.value = null;
}

function endGame(reactionTime) {
  score.value = reactionTime; 
  isPlaying.value = false;
}

function handleEnd(reactionTime) {
  endGame(reactionTime);
}

function tooSoon() {
  if (!isPlaying.value) return; // Si no se está jugando, no hagas nada
  
  const isBlockTargetShowing = document.querySelector('.blockTarget');
  if (!isBlockTargetShowing) {
    endGame(0.1);
  }
}

</script>

<style>
#app {
  margin: 0;
  height: 100vh;
  font-family: 'Roboto', sans-serif;
  font-weight: 400;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
}

.target{
  height: 100vh;
}

button {
  background: green;
  color: white;
  border: none;
  padding: 10px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
  transition: background 0.05s;
}

button:hover{
  background: darkgreen;
}

button:disabled{
  opacity: 0.5;
  cursor: not-allowed;
}

button:disabled:hover{
  background: green;
}
</style>
