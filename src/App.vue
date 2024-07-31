<script setup>
// script setup 寫法和cdn方式不同，不用return 

import { ref } from 'vue'
const num = ref(2)
//   console.log(num);
console.log(num.value)

function clickMe() {
  num.value++
}

// return { num, clickMe };
</script>

<template>
  <div>
    {{ num }}
    <button type="button" v-on:click="clickMe">點我</button>
  </div>
</template>
