<template>
  <div>
    <h1>v-bind with img (Composition API)</h1>
    <img :src="imgSrc" />
  </div>
</template>

<script setup>
import { ref } from 'vue'

const imgSrc = ref('https://upload.wikimedia.org/wikipedia/commons/9/95/Vue.js_Logo_2.svg')
</script>