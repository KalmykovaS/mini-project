<template>
  <div class="container mx-auto p-6">
    <div v-if="status === 'pending'" class="text-gray-500">Loading...</div>
    <template v-else>
      <p class="text-gray-700 text-lg">Post {{ id }}</p>
      <h1 class="text-3xl font-bold mb-4">{{ data?.title }}</h1>
      <p class="text-gray-600 leading-relaxed">{{ data?.body }}</p>
    </template>
  </div>
</template>

<script setup lang="ts">
definePageMeta({
  layout: 'post',
})

const route = useRoute();
const id = route.params.id;

type PostItem = {
  id: number;
  title: string;
  body: string;
}

const { public: { apiBase } } = useRuntimeConfig();

const { data, status } = await useFetch<PostItem>(`${apiBase}/posts/${id}`, { lazy: true });
console.log(data.value);

// использовать useFetch с номером id для вывода текста

// просто $fetch это обертка над fetch, который работает на сервере, он нам нужен только, если отправлять запросы на сервер (типа формы)
// код компонентов исполняется на клиенте и на сервере. useFetch и useAsyncData скачивают данные только один раз, когда на сервере создается страница, передаются на клиент они уже внутри html и когда nuxt создается на клиентской стороне данные заново не скачиваются (позволяет 2 раза не запрашивать данные)
</script>