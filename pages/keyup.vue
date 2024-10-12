<template>
  <div>
    <h1>간단한 Enter 이벤트 예제</h1>
    <input @keyup.enter="handleEnter" placeholder="Enter를 누르세요">
    <p>{{ message }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const message = ref('')

const handleEnter = () => {
  message.value = 'Enter 키가 눌렸습니다!'
}


</script>