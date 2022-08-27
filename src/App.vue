<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>

  <nav class="bg-purple-800">
    <div class="container mx-auto">
      <div class="flex items-center">
        <RouterLink to="/" class="inline-block text-purple-100 px-16 py-4 transition-colors hover:bg-purple-700 duration-300">
          Home 
        </RouterLink>
        <RouterLink to="/to-do" class="inline-block text-purple-100 px-16 py-4 transition-colors hover:bg-purple-700 duration-300">
          To do
        </RouterLink>
      </div>
    </div>
  </nav>
  <RouterView />

</template>
