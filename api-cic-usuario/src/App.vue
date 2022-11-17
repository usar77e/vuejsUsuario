<script setup>
  const name = 'Vue dinamico';
  const arrayFrutas = [
        {
            name: "Manzana",
            price: "$1.00",
            description: "Una manzana",
            id: 1,
        },
        {
            name: "Pera",
            price: "$2.00",
            description: "Una pera",
            id: 2,
        },
        {
            name: "Naranja",
            price: "$3.00",
            description: "Una naranja",
            id: 3,
        },
    ];
</script>

<template>
  <h1>Holas {{ name.toUpperCase() }} </h1>
  <br/>
  <ul>
    <li v-for="(fruta, index) in arrayFrutas"
    :key="fruta.id" >
      {{ index }} - Nombre: {{ fruta.name }}, Descripcion: {{fruta.description}}, precio: {{fruta.price}}
    </li>
  </ul>
</template>

<style>
  h1 {
    color: red;
  }
</style>