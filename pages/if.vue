<template>
  <div>
    <h1>v-if 예제</h1>
    <button @click="toggleVisibility">토글</button>
    
    <div v-if="isVisible">
      <p>이 텍스트는 보이거나 숨겨집니다.</p>
    </div>
    
    <div v-else>
      <p>isVisible이 false일 때 이 텍스트가 보입니다.</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const isVisible = ref(true)

const toggleVisibility = () => {
  isVisible.value = !isVisible.value
}
</script>