<script setup lang="ts">
import PageView from '../components/PageView.vue'
//classes
</script>

<template>
  <main class="content">
    <PageView :tabs="[
      {
        text: 'Primary',
        id: 'home-primary'
      },
      {
        text: 'Secondary',
        id: 'home-secondary'
      },
      {
        text: 'Tertiary',
        id: 'home-tertiary'
      }
    ]"/>
  </main>
</template>

<style scoped>
  .content {
    margin-left: 0.5rem;
    margin-right: 0.5rem;
  }
</style>
