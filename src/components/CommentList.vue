<template>
    <div class="comment-list">
      <h3>Comentarios</h3>
      <ul>
        <!-- Renderizar los comentarios -->
        <li v-for="(comment, index) in comments" :key="index">
          {{ comment.text }}
        </li>
      </ul>
    </div>
  </template>
  
  <script setup>
  // Recibir los comentarios como props
  const props = defineProps({
    comments: Array
  });
  </script>
  
  <style scoped>
  .comment-list {
    margin-top: 20px;
  }
  
  .comment-list ul {
    list-style-type: none;
    padding: 0;
  }
  
  .comment-list li {
    background: #f9f9f9;
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 5px;
  }
  </style>
  