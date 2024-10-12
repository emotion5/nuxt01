<template>
  <div>
    <h2>과일 목록</h2>
    <ul>
      <li v-for="fruit in fruits" :key="fruit">{{ fruit }}</li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const fruits = ref(['자두', '바나나', '체리', '딸기'])
</script>