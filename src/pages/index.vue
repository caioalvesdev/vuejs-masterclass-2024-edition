<script setup lang="ts">
import { usePageStore } from '@/stores/page';

usePageStore().pageData.title = 'Home Page'
</script>


<template>
  <h1>Home Page</h1>
</template>
