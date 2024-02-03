<template>
  <div class="config">
  Конфиг:
  <div>
    Кол-во примеров: {{ quantity }}
    <br/>
    Максимальное кол-во цифр в примере: {{ maxNumber }}
    <br/>
    Разрешить ответы с отрицательными числами: 
    {{ negativeAnswer ? 'Да' : 'Нет' }}
    <br/>
    Режим: {{ mode === 'Adventure' ? 'Продвинутый' : 'Стандартный' }}
  </div>
</div>
<InputsBlock
  @quantity="quantity = $event"
  @numbers="maxNumber = $event"
/>
<CheckBoxBlock
  @inp="negativeAnswer = $event"
/>
<Ratio
  @inp="mode = $event"
/>
<button @click="generate">Сгенерировать</button>
</template>

<script setup lang="ts">
import { ref } from "vue";
import CheckBoxBlock from "./components/CheckBoxBlock.vue";
import InputsBlock from "./components/InputsBlock.vue";
import Ratio from "./ui/Ratio.vue";

const quantity = ref(5)
const maxNumber = ref(1)
const negativeAnswer = ref(false)
const mode = ref('Default')

function generate() {
  for (let i = 0; i < quantity.value; i++) {
    const numFirst = Math.floor(1 + Math.random() * 100)
    const numSecond = Math.floor(1 + Math.random() * 100)
    const action = Math.random() * 10
    if (action < 2.5) {
      console.log(`${numFirst} + ${numSecond} = ${numFirst + numSecond}`)
    } else if (action > 2.5 && action < 5) {
      console.log(`${numFirst} - ${numSecond} = ${numFirst - numSecond}`)
    } else if (action > 5 && action < 7.5) {
      console.log(`${numFirst} * ${numSecond} = ${numFirst * numSecond}`)
    } else {
      console.log(`${numFirst} / ${numSecond} = ${numFirst / numSecond}`)
    }
  }
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

