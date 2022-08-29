<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>

<div class="flex h-screen flex-col">

  <!-- Navigation bar -->
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
  <!-- end of Navigation bar -->
  
  <!-- Main content -->
  <main class="relative mt-2">
    <RouterView />
  </main>
  <!-- end of Main content -->
  
  <!-- Footer -->
  <footer class="w-full mt-5 bg-purple-800">
    <div class="container mx-auto">
      <div class="m-2 text-center text-purple-100"> To do page </div>
    </div>
  </footer>
  <!-- end of Footer -->

</div>

</template>
