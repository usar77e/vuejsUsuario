<script setup >
  import { ref, computed, onMounted } from 'vue';
  import  ButtonCounter  from './components/ButtonCounter.vue';
  import BlogPost from './components/BlogPost.vue';
  import PaginatePost from './components/PaginatePost.vue';
  import LoadingSpinner from './components/LoadingSpinner.vue';

  const posts = ref([])

  const favorito = ref("");
  const postXpagina = 10;
  const inicio = ref(0);
  const fin = ref(10);

  const loading = ref(true);

  const cambiarFavorito = (title) => {
    favorito.value = title;
  }

  onMounted(async() => {
    try {
      const res = await fetch('https://jsonplaceholder.typicode.com/posts')  
      posts.value = await res.json();
    } catch(error){
      console.log(error);
    } finally {
      loading.value = false;
    }
  });


 /* fetch('https://jsonplaceholder.typicode.com/posts')
    .then((res) => res.json())
    .then((data) => {
      posts.value = data;
    })
    .finally(() => loading.value = false)
*/
    const next = () => {
      inicio.value = inicio.value + postXpagina;
      fin.value = fin.value + postXpagina;
    } 
    const preview = () => {
      inicio.value = inicio.value - postXpagina;
      fin.value = fin.value - postXpagina;
    } 

</script>

<template>
  <LoadingSpinner v-if="loading"/>
  <div class="container" v-else>
    <h1>APP</h1>
    <h2>Mi post favorito es: {{ favorito }}</h2>
    <PaginatePost @next="next" @preview="preview" :inicio="inicio" :fin="fin" :maxLength="posts.length" class="mb-2"/>
    <!--<ButtonCounter />-->
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