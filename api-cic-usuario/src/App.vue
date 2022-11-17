<script setup>
  const name = 'Vue dinamico';
  //metodo
  const handlelclick = (message) => {
    console.log(message);
  }
</script>

<template>
  <h1>Holas {{ name.toUpperCase() }} </h1>
  <br/>
  <button v-on:click.left="handlelclick('texto left')">Activame left</button>
  <button @click.middle="handlelclick('texto middle')">Activame middle</button>
  <button @click.right.prevent="handlelclick('texto right')">Activame right</button>
</template>

<style>
  h1 {
    color: red;
  }
</style>