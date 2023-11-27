<template>
<div v-if="isShowing" class="blockTarget" @click="stopTimer">
    Click me
</div>
</template>

<script setup>
import { defineProps, onMounted, ref} from 'vue';

const isShowing = ref(false);
const timer = ref(null);
const reactionTime = ref(0);

const props = defineProps({
  delay: {
    type: Number,
  },
  onEnd: Function
});

onMounted(() => {
    setTimeout(() => {
        isShowing.value = true;
        startTimer();
    }, props.delay);
});

function startTimer() {
    timer.value = setInterval(() => {
        reactionTime.value += 10;
    }, 10);
}

function stopTimer() {
    clearInterval(timer.value);
    props.onEnd(reactionTime.value);
}

</script>

<style scoped>
    .blockTarget {
        width: 400px;
        border-radius: 20px;
        font-size: 2rem;
        background-color: green;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
        font-family: 'Roboto', 'Helvetica Neue', 'Helvetica', 'Arial', sans-serif;
        font-weight: 400;
        user-select: none;
        cursor:pointer;
    }

    .blockTarget:hover{
        background-color: darkgreen;
    }
</style>