<!-- src/App.vue -->
<template>
  <div class="container mx-auto p-4">
    <UserList />
  </div>
  <div class="container mx-auto p-4">
    <PostList />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import UserList from './components/UserList.vue'
import PostList from './components/PostList.vue'

export default defineComponent({
  name: 'App',
  components: {
    UserList,
    PostList,
  },
})
</script>