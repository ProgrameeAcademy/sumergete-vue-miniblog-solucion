<template>
    <div class="blog-post">
      <!-- Selector de post -->
      <select v-model="selectedPostIndex" @change="loadSelectedPost">
        <option v-for="(post, index) in posts" :key="index" :value="index">{{ post.title }}</option>
      </select>
      <div v-if="selectedPost">
        <!-- Título del post -->
        <h2>{{ selectedPost.title }}</h2>
        <!-- Contenido del post -->
        <p>{{ selectedPost.content }}</p>
  
        <!-- Componente para mostrar los comentarios -->
        <CommentList :comments="selectedPost.comments" />
  
        <!-- Componente para agregar un nuevo comentario -->
        <CommentForm @add-comment="addComment" />
      </div>
    </div>
  </template>
  
  <script setup>
  // Importar los componentes necesarios
  import { ref, onMounted, watch } from 'vue';
  import CommentList from './CommentList.vue';
  import CommentForm from './CommentForm.vue';
  
  // Datos de los posts (se obtendrán de un archivo JSON)
  const posts = ref([]);
  const selectedPostIndex = ref(0);
  
  // Cargar los datos de los posts
  const loadPosts = async () => {
    const response = await fetch('/src/assets/posts.json');
    const data = await response.json();
    posts.value = data;
  };
  
  // Post seleccionado actualmente
  const selectedPost = ref(null);
  
  // Función para cargar el post seleccionado
  const loadSelectedPost = () => {
    selectedPost.value = posts.value[selectedPostIndex.value];
  };
  
  // Llamar a loadPosts al montar el componente
  onMounted(async () => {
    await loadPosts();
    loadSelectedPost();
  });
  
  // Función para agregar un comentario
  const addComment = (comment) => {
    selectedPost.value.comments.push({ text: comment });
  };
  
  // Actualizar el post seleccionado cuando cambia el índice seleccionado
  watch(selectedPostIndex, loadSelectedPost);
  </script>
  
  <style scoped>
  .blog-post {
    text-align: left;
    margin: 20px auto;
    width: 50%;
    border: 1px solid #ccc;
    padding: 20px;
    border-radius: 10px;
  }
  
  select {
    margin-bottom: 20px;
    padding: 10px;
    font-size: 16px;
    width: 100%;
  }
  </style>
  