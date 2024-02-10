<template>
  <div class="block-inputs">
  <Inp 
    @inp="$emit('quantity', $event)" 
    :min="5"
    title="Кол-во примеров"
  />
</div>
</template>

<script setup lang="ts">
import Inp from "../ui/Input.vue";
</script>

<style>

.block-inputs {
  display: grid;
  gap: 10px;
}

</style>