

<template>
  <div>
    <h1>v-bind array with button (Composition API)</h1>
    <button :class="buttonStyles.class" @click="handleClick">
      {{ buttonText }}
    </button>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const buttonText = ref('클릭하세요')

const buttonStyles = reactive({
  class: ['btn', 'btn-primary'],
})

const handleClick = () => {
  alert('버튼이 클릭되었습니다!')
}
</script>

<style scoped>
.btn {
  border: none;
  cursor: pointer;
  border-radius: 8px;
  transition: all 0.3s ease;
  width: 200px;
  height:60px;
  font-size: 24px;
}
.btn-primary {
  background-color: #3498db;
  color: white;
}
.btn-primary:hover {
  background-color: #2980b9;
  transform: scale(1.05);
}
</style>
