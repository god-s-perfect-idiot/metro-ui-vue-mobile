<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import AppBar from './components/AppBar.vue'
import AppTitle from './components/fragments/AppTitle.vue'
// import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <RouterLink to="/">
      <AppTitle text="Metro UI Vue Mobile"/>
    </RouterLink>
  </header>

  <RouterView />
  <footer>
    <AppBar :iconButtons="[{title: 'fa-solid fa-info', route: '/about'}]"/>
  </footer>
</template><i class=""></i><i class=""></i>

<style scoped>
</style>
