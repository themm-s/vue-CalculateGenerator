<template>
  <div class="answer-block">
    <div v-for="example, index in examples" class="answer-question">
      <label>{{ example }} =
      <input
        :class="{
          'answer-input': true,
          'correct': valid[index] || false
        }"
        type="text"
        @input="checkResult(index, ($event.target as HTMLInputElement)?.value)"
        :key="index"
      />
    </label>
    </div>    
  </div>

</template>

<script setup lang="ts">
import { computed, ref } from 'vue';

const props = defineProps<{
  examples: string[];
  answer: string[];
}>()

const valid = ref<boolean[]>([])
const answer = computed(() => props.answer)

function checkResult(i: number, value?: string) {
  valid.value[i] = value == answer.value[i]
  return value == answer.value[i]
}

</script>

<style>
label {
  display:flex;
}

.answer-block {
  display: grid;
  grid-template: 1fr 1fr 1fr 1fr;
  gap: 10px;
  /* height: 100vh */
}

.answer-question {
  width: 100%;
  padding: 4px;
  border: 1px solid gray;
  border-radius: 5px;
  margin-bottom: 20px;
}

.correct {
  border-color: green;
}

/* .answer-input:not(.correct) {
  border-color: red;
} */

.answer-input {
  margin-left: auto;
  outline: none;
}
</style>