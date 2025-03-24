<template>
  <header class="bg-gray-800 header">
    <div class="flex justify-between items-center mx-auto header__container max-w-5xl">
      <nav class="flex gap-8">
        <NuxtLink to="/" class="text-gray-400 text-xl font-bold hover:text-white">Home</NuxtLink>
        <NuxtLink to="/posts" class="text-gray-400 text-xl font-bold hover:text-white">Posts</NuxtLink>
      </nav>
    </div>
  </header>
  <main>
    <slot/>
  </main>
  <footer class="bg-gray-900 text-gray-400 text-center p-2">mini-project, {{ currentYear }}</footer>
</template>

<script setup lang="ts">

const currentYear = ref<number>(new Date().getFullYear());
</script>