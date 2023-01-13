<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList v-if="showPosts" :posts="posts" />
    </div>
    <div v-else>Loading...</div>
    
    <button @click="showPosts = !showPosts">Toggle posts</button>
    <button @click="posts.pop()">Delete a post</button>
  </div>
</template>

<script setup>
import PostList from '@/components/PostList.vue'
import getPosts from '../composables/getPosts'
import { ref } from 'vue'

const name = 'HomeView';
const { posts, error, load } = getPosts();
load();
const showPosts = ref(true);
</script>
