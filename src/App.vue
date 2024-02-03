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
<button @click="Generate">Сгенерировать</button>
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

function Action() {

}

function Generate() {
  const arr = []
  for (let i = 0; i < quantity.value; i++) {
    const numFirst = Math.floor(1 + Math.random() * 100)
    const numSecond = Math.floor(1 + Math.random() * 100)
    const operator = ['+', '-', '/', '*'][Math.floor(Math.random() * 4)]
    arr.push(`${numFirst} ${operator} ${numSecond} = ${eval(numFirst + operator + numSecond)}`)
    console.log(arr)
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

