<script setup lang="ts">
const router = useRouter()
const { t } = useI18n()
</script>

<template>
  <main w-full min-h-full p="x4 y10" text="center gray-700 dark:gray-200" bg="gray-100 dark:black">
    <div text-4xl>
      <div i-carbon-warning inline-block />
    </div>
    <RouterView />
    <div>
      <button btn text-sm m="3 t8" @click="router.back()">
        {{ t('button.back') }}
      </button>
    </div>
  </main>
</template>
