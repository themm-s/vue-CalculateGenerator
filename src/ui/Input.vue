<template>
  <p>{{ title }}</p>
  <input 
    type="number" 
    placeholder="Выберите число"
    :min="min"
    max="100" 
    @input="$emit('inp', ($event.target as HTMLInputElement).value)" 
  />
</template>

<script setup lang="ts">

defineProps<{
  title: string,
  min: number
}>()

</script>