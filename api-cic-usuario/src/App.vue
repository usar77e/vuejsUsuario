<script setup>
  import { ref } from 'vue'
  const name = 'Vue dinamico';

  const counter = ref(0);
  const arrayColor = ["red", "green"];

  const increment = () => {
    console.log('aumentar contador');
    counter.value ++;
    console.log(counter);
  }
  
  const decrement = () => {
    console.log('disminuir contador');
    counter.value --;
    console.log(counter);
  }

  const reset = () => {
    console.log('aumentar contador');
    counter.value = 0;
    console.log(counter);
  }
  
  
</script>

<template>
  <h2 v-if="counter > 0" :style="`color:${arrayColor[1]}`">{{ counter }}</h2>
  <h2 v-else :style="`color:${arrayColor[0]}`">{{ counter }}</h2>
  
  <button @click="increment">Aumentar</button>
  <button @click="decrement">Disminuir</button>
  <button @click="reset">reset</button>
</template>

<style>
  h1 {
    color: red;
  }
</style>