<!-- src/components/UserList.vue -->
<template>
    <div>
      <h1 class="text-2xl font-bold">User List</h1>
      <ul>
        <li v-for="user in users" :key="user.id">
          {{ user.name }}
        </li>
      </ul>
    </div>
  </template>

  <script lang="ts">
  import { defineComponent } from 'vue'
  import { useQuery } from '@tanstack/vue-query'
  import axios from 'axios'

  interface User {
    id: number
    name: string
  }

  export default defineComponent({
    name: 'UserList',
    setup() {
      const { data } = useQuery<User[]>({
        queryKey: ['users'],
        queryFn: async () => {
          const response = await axios.get('https://jsonplaceholder.typicode.com/users')
          return response.data
        },
      })

      return {
        users: data,
      }
    },
  })
  </script>

  <style scoped>
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    padding: 8px;
    border-bottom: 1px solid #ccc;
  }
  </style>