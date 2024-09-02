<template>
  <div class="result">
    <div class="title">{{ props.results[resultIndex].title }}</div>
    <div class="desc">{{ props.results[resultIndex].desc }}</div>
  </div>
</template>

<script setup>
import { computed, defineProps } from "vue";
const props = defineProps(['results', 'totalCorrect'])

const resultIndex = computed(() => {
  let index = 0;
  props.results.forEach((e, i) => {
    if (e.min <= props.totalCorrect && e.max >= props.totalCorrect) {
      index = i;
    }
   
  });
  return index;
});
</script>

<style></style>
