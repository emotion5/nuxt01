<template>
  <div>
    <h1>v-html 예제 (Composition API)</h1>
    <div v-html="htmlContent"></div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const htmlContent = ref('<h2>이것은 <strong>HTML</strong> 내용입니다.</h2>')
</script>