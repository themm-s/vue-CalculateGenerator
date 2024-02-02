<template>
  <p>{{ title }}</p>
  <input type="checkbox" @input="$emit('inp', ($event.target as HTMLInputElement).checked)" />
</template>

<script setup lang="ts">

defineProps<{
  title: string
}>()

</script>