<template>
  <div v-if="answerComponent">
    <Config
      :quantity=quantity
      :maxNumber=maxNumber
      :negativeAnswer=negativeAnswer
      :mode=mode
    />
    
    <InputsBlock @quantity="quantity = $event" @numbers="maxNumber = $event" />
    <CheckBoxBlock @inp="negativeAnswer = $event" />
    <Ratio @inp="mode = $event" />
    <button @click="Generate">Сгенерировать</button>
  </div>
  <div v-else>
    <TableOfAnswers :answer="answer" :examples="examples"/>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import CheckBoxBlock from "./components/CheckBoxBlock.vue";
import Config from "./components/Config.vue"

import InputsBlock from "./components/InputsBlock.vue";
import Ratio from "./ui/Ratio.vue";
import TableOfAnswers from "./components/TableOfAnswers.vue";

const quantity = ref(5);
const maxNumber = ref(1);
const negativeAnswer = ref(false);
const answerComponent = ref(true);
const mode = ref('Default');
const examples: string[] = [];
const answer: string[] = [];

function Generate() {
  examples.splice(0, examples.length);
  for (let i = 0; i < quantity.value; i++) {
    const numFirst = Math.floor(1 + Math.random() * 100);
    const numSecond = Math.floor(1 + Math.random() * 100);

    let operator = ['+', '-'][Math.floor(Math.random() * 2)];

    if (mode.value === 'Adventure') {
      operator = ['+', '-', '/', '*'][Math.floor(Math.random() * 4)];
    }

    let result = eval(numFirst + operator + numSecond).toFixed(1);

    if (result < 0 && !negativeAnswer.value) { i--; continue; }
    if (result.includes('.') && result.split('.')[1] == '0') { result = result.split('.')[0]; }
    answer.push(result);

    examples.push(`${numFirst} ${operator} ${numSecond}`);
    console.log(examples);
  }
  answerComponent.value = false;
}

</script>

<style>
.config {
  margin: auto;
  width: 600px;
  word-break: break-all;
  padding: 12px;
  border: 1px solid gray;
  border-radius: 5px;
  margin-bottom: 20px;
}
</style>

