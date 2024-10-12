<template>
  <div>   
    <p>{{ message }}</p>    
  </div>
</template>

<script setup>
import { ref } from 'vue'
const message = ref('안녕하세요, 민!')
</script>

