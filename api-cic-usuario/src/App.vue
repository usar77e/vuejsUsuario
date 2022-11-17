<script setup >
  import { ref } from 'vue';
  import  ButtonCounter  from './components/ButtonCounter.vue';
  import BlogPost from './components/BlogPost.vue';
  import PaginatePost from './components/PaginatePost.vue';

  const posts = ref([])

  const favorito = ref("");
  const postXpagina = 10;
  const inicio = ref(0);
  const fin = ref(10);

  const cambiarFavorito = (title) => {
    favorito.value = title;
  }

  fetch('https://jsonplaceholder.typicode.com/posts')
    .then((res) => res.json())
    .then((data) => {
      posts.value = data;
    })

    const next = () => {
      inicio.value = inicio.value + postXpagina;
      fin.value = fin.value + postXpagina;
    } 
    const preview = () => {
      inicio.value = inicio.value - postXpagina;
      fin.value = fin.value - postXpagina;
    } 

</script>

<template class="container">
  <div >
    <h1>APP</h1>
    <h2>Mi post favorito es: {{ favorito }}</h2>
    <PaginatePost class="mb-2"/>
    <button @click="preview" :disabled="inicio === 0">PREVIEW P</button>
    <button @click="next">NEXT P</button>
    <ButtonCounter/>
    <BlogPost class="mb-1" style="color:black" 
      v-for="post in posts.slice(inicio, fin)"
      :title="post.title"
      :id="post.id"
      :body = "post.body"
      :colorText="post.colorText"
      @cambiarFavoritoNombre="cambiarFavorito"
    />
  </div>
  
</template>