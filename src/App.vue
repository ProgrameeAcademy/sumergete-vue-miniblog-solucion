<template>
  <div id="app">
    <h1>Mini Blog</h1>
    <BlogPost />
  </div>
</template>

<script setup>
// Importar el componente BlogPost
import BlogPost from './components/BlogPost.vue';
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 50px;
}
</style>
