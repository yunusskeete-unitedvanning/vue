<template>
    <div class="post">
        <router-link :to="{ name: 'Details', params: { id: post.id}}">
            <h3>{{ post.title }}</h3>
        </router-link>
        <p>{{ snippet }}</p>
        <span v-for="tag in post.tags" :key="tag">
            #{{ tag }}
        </span>
    </div>
</template>
    
<script setup>
import { computed } from 'vue'
const props = defineProps(['post']);
const snippet = computed(() => {
    return props.post.body.substring(0, 100) + '...' // return the first 100 characters of the string
});
</script>


<style>

</style>