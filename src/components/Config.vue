<template>
  <div class="config">
    Конфиг:
    <div>
      Кол-во примеров: {{ quantity }}
      <br />
      Максимальное кол-во цифр в примере: {{ maxNumber }}
      <br />
      Разрешить ответы с отрицательными числами:
      {{ negativeAnswer ? 'Да' : 'Нет' }}
      <br />
      Режим: {{ mode === 'Adventure' ? 'Продвинутый' : 'Стандартный' }}
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps<{
  quantity: number,
  maxNumber: number,
  negativeAnswer: boolean,
  mode: string
}>();

const quantity = computed(() => props.quantity);
const maxNumber = computed(() => props.maxNumber);
const negativeAnswer = computed(() => props.negativeAnswer);
const mode = computed(() => props.mode);
</script>

<style scoped>
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


