<template>
<p v-if="props.score !== 0.1">Your score is - {{ props.score }}ms! </p>
<p v-if="props.score === 0.1">You clicked too soon! </p>
<p class="rank" v-if="props.score !== 0.1">{{ rank }} </p>
</template>

<script setup>
import { defineProps, ref, onMounted} from 'vue';

const rank = ref(null);

const props = defineProps({
  score: {
    type: Number,
  }
});

onMounted(() => {
    if(props.score < 200) {
        rank.value = 'Godlike';
    } else if (props.score < 250) {
        rank.value = 'Great';
    } else if (props.score < 300) {
        rank.value = 'Good';
    } else if (props.score < 350) {
        rank.value = 'Average';
    } else if (props.score < 400) {
        rank.value = 'Bad';
    } else {
        rank.value = 'Terrible';
    }
});

</script>

<style scoped> 
.rank {
    font-size: 1.4rem;
    font-weight: 500;
}
</style>