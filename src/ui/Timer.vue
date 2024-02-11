<template>
  <h1>{{ time }}</h1>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue';

const props = defineProps<{
  checkValid: boolean
}>();

const valid = computed(() => props.checkValid)
const time = ref("00:00.000");
let [milliseconds,seconds,minutes] = [0,0,0];

setInterval(() => {
    timer()
  }, 10)

function timer() {
  if(!valid.value) {
    milliseconds+=10;
    if(milliseconds == 1000){
        milliseconds = 0;
        seconds++;
        if(seconds == 60){
            seconds = 0;
            minutes++;
        }
    }
  }
  let m = minutes < 10 ? "0" + minutes : minutes;
  let s = seconds < 10 ? "0" + seconds : seconds;
  let ms = milliseconds < 10 ? "00" + milliseconds : milliseconds < 100 ? "0" + milliseconds : milliseconds;
  time.value = `${m} : ${s} : ${ms}`
}

</script>