<template>
  <div class="block-radio">
    <label for="Default">
    <input type="radio" checked name="radio" value="Default" id="Default" @change="$emit('inp', 'Default')" />
    Стандартный режим (+ -)
  </label>
  <label for="Adventure">
    <input type="radio" name="radio" value="Adventure" id="Adventure" @change="$emit('inp', 'Adventure')" />
    Продвинутый режим (+ - * /)
  </label>
  </div>
</template>

<style>
.block-radio {
  display: flex;
  justify-content: center;
  flex-direction: column;
}
</style>