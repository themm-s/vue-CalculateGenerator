<template>
  <div class="config">
  Конфиг:
  <div>
    Кол-во примеров: {{ quantity }}
    <br/>
    Минимальное кол-во цифр в примере: {{ minNumber }}
    <br/>
    Разрешить ответы с отрицательными числами: 
    {{ negativeAnswer ? 'Да' : 'Нет' }}
  </div>
</div>
<InputsBlock
  @quantity="quantity = $event"
  @numbers="minNumber = $event"
/>
<CheckBoxBlock
  @inp="negativeAnswer = $event"
/>
</template>

<script setup lang="ts">
import { ref } from "vue";
import CheckBoxBlock from "./components/CheckBoxBlock.vue";
import InputsBlock from "./components/InputsBlock.vue";

const quantity = ref(5)
const minNumber = ref(1)
const negativeAnswer = ref(false)

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

