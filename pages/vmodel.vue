<template>
  <div>
    <h1>v-model (Composition API)</h1>
    <input v-model="inputText" placeholder="텍스트를 입력하세요">
    <p>{{ inputText }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const inputText = ref('')
</script>