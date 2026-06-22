<!-- src/App.vue -->
<script setup lang="ts">
import TodoList from './components/TodoList.vue'
import WelcomeMessage from './components/WelcomeMessage.vue'
</script>

<template>
  <main>
    <WelcomeMessage msg="Webエンジニアになろう講習会へようこそ" />
    <TodoList />
  </main>
</template>

<style scoped>
main {
  padding: 2rem;
}
</style>