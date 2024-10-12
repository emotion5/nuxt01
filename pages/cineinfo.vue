<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const API_URL = 'http://localhost:4000/movies'
const movies = ref([])
const newMovie = ref({ title: '', director: '', year: '', rating: '' })
const editingMovie = ref(null)

// 모든 영화 가져오기
const fetchMovies = async () => {
  try {
    const response = await axios.get(API_URL)
    movies.value = response.data
  } catch (error) {
    console.error('Error fetching movies:', error)
  }
}

// 새 영화 추가
const addMovie = async () => {
  try {
    const response = await axios.post(API_URL, newMovie.value)
    movies.value.push(response.data)
    newMovie.value = { title: '', director: '', year: '', rating: '' }
  } catch (error) {
    console.error('Error adding movie:', error)
  }
}

// 영화 삭제
const deleteMovie = async (id) => {
  try {
    await axios.delete(`${API_URL}/${id}`)
    movies.value = movies.value.filter(movie => movie.id !== id)
  } catch (error) {
    console.error('Error deleting movie:', error)
  }
}

// 영화 수정 모드 시작
const startEdit = (movie) => {
  editingMovie.value = { ...movie }
}

// 영화 수정 저장
const saveEdit = async () => {
  try {
    const response = await axios.put(`${API_URL}/${editingMovie.value.id}`, editingMovie.value)
    const index = movies.value.findIndex(m => m.id === editingMovie.value.id)
    movies.value[index] = response.data
    editingMovie.value = null
  } catch (error) {
    console.error('Error updating movie:', error)
  }
}

// 컴포넌트 마운트 시 영화 목록 가져오기
onMounted(fetchMovies)
</script>

<template>
  <div>
    <h1>영화 목록</h1>
    
    <!-- 새 영화 추가 폼 -->
    <div>
      <input v-model="newMovie.title" placeholder="제목">
      <input v-model="newMovie.director" placeholder="감독">
      <input v-model="newMovie.year" placeholder="개봉년도" type="number">
      <input v-model="newMovie.rating" placeholder="평점" type="number" step="0.1">
      <button @click="addMovie">추가</button>
    </div>

    <!-- 영화 목록 -->
    <ul>
      <li v-for="movie in movies" :key="movie.id">
        <template v-if="editingMovie && editingMovie.id === movie.id">
          <input v-model="editingMovie.title">
          <input v-model="editingMovie.director">
          <input v-model="editingMovie.year" type="number">
          <input v-model="editingMovie.rating" type="number" step="0.1">
          <button @click="saveEdit">저장</button>
        </template>
        <template v-else>
          {{ movie.title }} - {{ movie.director }} ({{ movie.year }}) 평점: {{ movie.rating }}
          <button @click="startEdit(movie)">수정</button>
          <button @click="deleteMovie(movie.id)">삭제</button>
        </template>
      </li>
    </ul>
  </div>
</template>