<script setup>
  const name = 'Vue dinamico';
  const styleColor = "color: blue";
  const arrayColores = ["blue", "red", "peru"];
  const activo = true;
</script>

<template>
  <h1>Hola {{ name.toUpperCase() }} </h1>
  <br/>
  <h2 :style="styleColor">Soy azul</h2>
  <br/>
  <h2 :style="`color: ${arrayColores[2]}`" > {{ arrayColores }}</h2>
  <br/>
  <h2>
    {{ activo ? "Estoy activo" : "Estoy inactivo" }}
  </h2>
  <br/>
  <p v-if="activo">Estoy activo</p>
  <p v-else="activo">Estoy inactivo</p>
  <h1>variacion de if</h1>
  <p v-if="activo === true">Estoy activo</p>
  <p v-else-if="activo === false">Estoy inactivo</p>
  <p v-else>Estoy indeciso</p>
  <h1>v-show</h1>
  <h2 v-show="activo">Estoy activo v-show</h2>
</template>

<style>
  h1 {
    color: red;
  }
</style>