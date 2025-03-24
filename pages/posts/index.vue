<template>
  <div class="container mx-auto p-6">
    <h1 class="text-3xl font-bold mb-4">All posts</h1>
    <div v-if="status === 'pending'" class="text-gray-500">Loading...</div>
    <ul v-else class="space-y-2">
      <li v-for="post in data" :key="post.id">
        <NuxtLink
            :to="{ name: 'posts-id', params: { id: post.id } }"
            class="text-gray-600 hover:text-blue-800 transition-colors"
        >
          {{ post.title }}
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
type Post = {
  id: number;
  title: string;
  body: string;
}
const { public: { apiBase } } = useRuntimeConfig();

const { data, status } = await useFetch<Post[]>(`${apiBase}/posts`, { lazy: true });
</script>

<style lang="scss" scoped>

</style>