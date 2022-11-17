<script setup >
  import { ref } from 'vue';
  import  ButtonCounter  from './components/ButtonCounter.vue';
  import BlogPost from './components/BlogPost.vue';


  const posts = ref([
    {title: 'Post 1', id: 1, body: 'descripcion larga1', colorText: 'primary'},
    {title: 'Post 2', id: 2, body: 'descripcion 2', colorText: 'secondary'},
    {title: 'Post 3', id: 3, body: 'descripcion 3', colorText: 'success'},
    {title: 'Post 4', id: 4, body: 'descripcion 4', colorText: 'primary'},
  ])
</script>

<template>
  <div class="container">
    <h1>APP</h1>
    <ButtonCounter/>
    <BlogPost v-for="post in posts"
      :title="post.title"
      :id="post.id"
      :body = "post.body"
      :colorText="post.colorText"
    />
  </div>
  
</template>