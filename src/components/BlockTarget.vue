<template>
<div v-if="isShowing" class="block">
    click me
</div>
</template>

<script setup>
import { defineProps, onMounted, ref} from 'vue';

const isShowing = ref(false);

const props = defineProps({
    delay: {
        type: Number,
    }
})

onMounted(() => {
    setTimeout(() => {
        isShowing.value = true;
    }, props.delay);
});

console.log('delay', props.delay);

</script>

<style scoped>
    .block {
        width: 400px;
        border-radius: 20px;
        background-color: crimson;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>