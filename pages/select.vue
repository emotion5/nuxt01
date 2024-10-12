<template>
  <div>
    <h1>v-model with Select (Composition API)</h1>
    <select v-model="selectedFruit">
      <option value="">과일을 선택하세요</option>
      <option value="apple">사과</option>
      <option value="banana">바나나</option>
      <option value="cherry">체리</option>
    </select>
    <p>선택한 과일: {{ selectedFruit }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const selectedFruit = ref('')
</script>