<script setup lang="ts">
// https://github.com/vueuse/head
// you can use this to manipulate the document head in any components
useHead({
  title: 'Vitesse-antd',
  meta: [
    { name: 'description', content: 'Opinionated Vite Starter Template' },
  ],
})
</script>

<template>
  <RouterView />
</template>
