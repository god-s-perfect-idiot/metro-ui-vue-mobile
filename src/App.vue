<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import AppBar from './components/AppBar.vue'
// import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <!-- <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div> -->
    
  </header>

  <RouterView />
  <footer>
    <AppBar :iconButtons="[{title: 'fa-solid fa-info', route: '/about'}]"/>
  </footer>
</template><i class=""></i><i class=""></i>

<style scoped>
</style>
