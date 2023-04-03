<template>
    <div>
        <h1>
            users component
        </h1>

        <div v-for="user in users" :key="user.id">
            <h1>{{ user.name }}</h1>
            <p>{{ user.email }}</p>
        </div>
    </div>
</template>



<script setup lang="ts">

import {ref, onMounted} from 'vue'

interface User {
  id: number
  name: string
  username: string
  email: string
}

const users = ref<User[]>([])

onMounted(async () => {
  const response = await fetch('https://jsonplaceholder.typicode.com/users')
  const fetchedUsers = await response.json()
  users.value = fetchedUsers
})

</script>