<script setup lang="ts">
import { NotionRenderer, getPageBlocks } from 'vue3-notion'

const blockMap = ref()

onMounted(async () => {
  blockMap.value = await getPageBlocks(import.meta.env.VITE_PAGE_ID)
})
</script>

<template>
  <div v-if="!blockMap" class="fixed top-5 right-5 loader" />

  <NotionRenderer v-if="blockMap" :block-map="blockMap" full-page />
</template>

