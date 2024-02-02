<template>
  <div class="checkboxs-block">
<CheckBox 
  @inp="$emit('inp', $event)"
  title="Разрешить ответы с отрицательными числами" 
/>
</div>
</template>

<script setup lang="ts">
import CheckBox from "../ui/CheckBox.vue";

</script>

<style>
.checkboxs-block {
  display: flex;
  justify-content: center;
  gap: 10px;
}
</style>