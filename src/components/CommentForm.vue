<template>
    <div class="comment-form">
      <h3>Añadir un comentario</h3>
      <form @submit.prevent="submitComment">
        <!-- Campo para el nuevo comentario -->
        <textarea v-model="newComment" placeholder="Escribe un comentario"></textarea>
        <!-- Botón para enviar el comentario -->
        <button type="submit">Enviar</button>
      </form>
    </div>
  </template>
  
  <script setup>
  // Importar ref desde Vue
  import { ref } from 'vue';
  
  // Crear una referencia para el nuevo comentario
  const newComment = ref('');
  
  // Emitir el evento para agregar un comentario
  const emit = defineEmits(['add-comment']);
  
  const submitComment = () => {
    if (newComment.value.trim()) {
      emit('add-comment', newComment.value);
      newComment.value = '';
    }
  };
  </script>
  
  <style scoped>
  .comment-form {
    margin-top: 20px;
  }
  
  .comment-form textarea {
    width: 100%;
    height: 100px;
    padding: 10px;
    margin-bottom: 10px;
  }
  
  .comment-form button {
    padding: 10px 20px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .comment-form button:hover {
    background-color: #0056b3;
  }
  </style>
  