<script setup>
  import { ref, computed } from 'vue'
  const name = 'Vue dinamico';

  const counter = ref(0);
  const arrayColor = ["red", "green"];

  const arrayFavoritos = ref([]);

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

  const classEstado = computed(() => {
    const resultado = arrayFavoritos.value.find( num => num === counter.value);
    //console.log("rres -> "  + resultado);
    if(resultado === 0) return true;
    return resultado ? true : false;
  })

  const add = () => {
    arrayFavoritos.value.push(counter.value);
    console.log(arrayFavoritos);
  }

</script>

<template>
  <div class="container">
    <h2 :class="classCounter">{{ counter }}</h2>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Aumentar</button>
      <button @click="decrement" class="btn btn-danger">Disminuir</button>
      <button @click="reset" class="btn btn-secondary">reset</button>
      <button :disabled="classEstado" @click="add" class="btn btn-primary">agregar</button>
    </div>
    
    <h1>Numeros seleccionados por el usuario</h1>
    <ul class="list-group">
      <li v-for="(fav, index) in arrayFavoritos"
      :key="index" class="list-group-item">
        {{ fav }}
      </li>
    </ul>

  </div>
  
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