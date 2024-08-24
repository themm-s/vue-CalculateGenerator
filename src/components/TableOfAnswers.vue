<template>
  <div class="timer" v-if="second > 0">
      <h1>{{ second }}</h1>
    </div>
  <div v-else class="answer-block">
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
  <div v-if="second == 0">
    <Timer :checkValid=answersCorrect />
    <button @click="props.switch()">Назад</button>
  </div>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue';
import Timer from '../ui/Timer.vue';

const props = defineProps<{
  switch: () => void;
  examples: string[];
  answer: string[];
}>()

const valid = ref<boolean[]>([])
const answer = computed(() => props.answer)
const second = ref(5)
const answersCorrect = ref(false)

setInterval(() => {
  if(props.examples.length == valid.value.length && valid.value.every(x => x == true)) {
    answersCorrect.value = true
    console.log(answersCorrect.value)
  }
  if (second.value > 0)
  second.value -= 1
}, 1000)

function checkResult(i: number, value?: string) {
  valid.value[i] = value == answer.value[i]
  console.log(valid.value)
  return value == answer.value[i]
}

</script>

<style>
.timer {
  display: flex;
  justify-content: center;
  padding: 1rem;
}

label {
  display:flex;
}

.answer-block {
  display: grid;
  grid-template: repeat(3, 1fr) / repeat(2, 1fr) repeat(2, 1fr);
  gap: 30px;
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