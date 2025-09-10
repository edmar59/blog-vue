<!-- src/views/PostCreate.vue -->
<script setup>
import { ref } from 'vue'
import { usePostsStore } from '@/stores/posts'

const store = usePostsStore()
const title = ref('')
const body = ref('')

function createPost() {
  if (!title.value || !body.value) return
  store.addPost({ title: title.value, body: body.value })
  title.value = ''
  body.value = ''
  alert('Post created!')
}
</script>

<template>
  <div class="create-form">
    <h2>Create a New Post</h2>
    <form @submit.prevent="createPost">
      <input v-model="title" type="text" placeholder="Post title" />
      <textarea v-model="body" placeholder="Write something..."></textarea>
      <button type="submit">Save</button>
    </form>
  </div>
</template>

<style scoped>
.create-form {
  max-width: 600px;
  margin: 2rem auto;
  padding: 1rem;
  border: 1px solid #ddd;
  border-radius: 8px;
}
input,
textarea {
  display: block;
  width: 100%;
  margin: 0.5rem 0;
  padding: 0.5rem;
}
button {
  background: #1e40af;
  color: white;
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  background: #2563eb;
}
</style>
