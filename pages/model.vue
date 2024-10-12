<template>
  <div>
    <input v-model="name" placeholder="이름을 입력하세요">
    <p>안녕하세요, {{ name }}!</p>
  </div>
</template>
  
<script setup>
  import { ref } from 'vue'
  
  const name = ref('')
</script>