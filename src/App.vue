<template>
  <div class="app">
    <Designer />
  </div>
</template>

<script setup>
import Designer from './components/Designer.vue'
</script>

<style>
body { margin: 0; font-family: sans-serif; }
.app { display: flex; flex-direction: row; height: 100vh; }
</style>