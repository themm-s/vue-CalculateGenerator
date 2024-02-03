<template>
  {{ test = answer }}
  <div v-for="example, index in examples">
    <label>{{ example }} =
    <input 
      type="number" 
      @input="checkResult(index)" 
      :key="index" 
    />
  </label>
  </div>
</template>

<script setup lang="ts">

defineProps<{
  examples: string[];
  answer: string[];
}>()

let test: string[] = []
setTimeout(() => {
  console.log(test)
}, 5000);

</script>