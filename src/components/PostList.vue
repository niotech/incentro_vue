<template>
  <div>
    <h1 class="text-2xl font-bold mb-4">Posts</h1>
    <ul>
      <li v-for="post in posts" :key="post.id" class="mb-2">
        <h2 class="text-xl font-semibold">{{ post.title }}</h2>
        <p>{{ post.body }}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { useQuery } from '@tanstack/vue-query'
import axios from 'axios'

interface Post {
  id: number
  title: string
  body: string
}

export default defineComponent({
  name: 'PostList',
  setup() {
    const { data } = useQuery<Post[]>({
      queryKey: ['posts'],
      queryFn: async () => {
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts')
        return response.data
      },
    })

    return {
      posts: data,
    }
  },
})
</script>

<style scoped>
.mb-2 {
  margin-bottom: 0.5rem;
}
</style>