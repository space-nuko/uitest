<script setup lang="ts">
import 'core-js/stable';
import 'regenerator-runtime/runtime';
import Editor from './components/Editor.vue'
</script>

<template>
  <Editor />
</template>

<script lang="ts">
export default {
  name: 'App',
  components: {
    Editor
  }
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
