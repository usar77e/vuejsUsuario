<script setup>
  import { ref, computed } from 'vue'
  const name = 'Vue dinamico';

  const counter = ref(0);
  const arrayColor = ["red", "green"];

  const increment = () => counter.value ++;
  
  const decrement = () => counter.value --

  const reset = () => counter.value = 0;
  
  const classCounter = computed (()=> {
    if(counter.value == 0) {
      return 'zero'
    }
    if(counter.value > 0) {
      return 'positive'
    }
    if(counter.value < 0) {
      return 'negative'
    }
  }) 
</script>

<template>
  <h2 :class="classCounter">{{ counter }}</h2>

  <button @click="increment">Aumentar</button>
  <button @click="decrement">Disminuir</button>
  <button @click="reset">reset</button>
</template>

<style>
  h1 {
    color: red;
  }
  .positive {
    color: green;
  }
  .negative {
    color:red;
  }
  .zero {
    color: peru;
  }
</style>