<template>
  <div ref="container"></div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import * as THREE from 'three'
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls'

const container = ref(null)
let scene, camera, renderer, controls, icosahedron

// 씬 초기화 함수
const initScene = () => {
  // 씬 생성
  scene = new THREE.Scene()
  
  // 카메라 설정
  camera = new THREE.PerspectiveCamera(
    75,
    window.innerWidth / window.innerHeight,
    0.1,
    1000
  )
  camera.position.z = 5
  
  // 렌더러 설정
  renderer = new THREE.WebGLRenderer({ antialias: true })
  renderer.setSize(window.innerWidth, window.innerHeight)
  renderer.setPixelRatio(window.devicePixelRatio)
  container.value.appendChild(renderer.domElement)
  
  // OrbitControls 추가
  controls = new OrbitControls(camera, renderer.domElement)
  controls.enableDamping = true
  
  // DirectionalLight 추가
  const directionalLight = new THREE.DirectionalLight(0xffffff, 1)
  directionalLight.position.set(5, 5, 5)
  scene.add(directionalLight)
  
  // 환경광 추가
  const ambientLight = new THREE.AmbientLight(0x404040)
  scene.add(ambientLight)
  
  // 정이십면체 생성
  const geometry = new THREE.IcosahedronGeometry(1, 0)
  const material = new THREE.MeshPhongMaterial({
    color: 0x00ff00,
    wireframe: false,
    flatShading: true
  })
  icosahedron = new THREE.Mesh(geometry, material)
  scene.add(icosahedron)
}

// 애니메이션 함수
const animate = () => {
  requestAnimationFrame(animate)
  
  // 정이십면체 회전
  icosahedron.rotation.x += 0.01
  icosahedron.rotation.y += 0.01
  
  controls.update()
  renderer.render(scene, camera)
}

// 윈도우 리사이즈 핸들러
const handleResize = () => {
  camera.aspect = window.innerWidth / window.innerHeight
  camera.updateProjectionMatrix()
  renderer.setSize(window.innerWidth, window.innerHeight)
}

// 컴포넌트 마운트 시 초기화
onMounted(() => {
  initScene()
  animate()
  window.addEventListener('resize', handleResize)
})

// 컴포넌트 언마운트 시 정리
onBeforeUnmount(() => {
  window.removeEventListener('resize', handleResize)
  controls.dispose()
  renderer.dispose()
})
</script>

<style scoped>
div {
  width: 100%;
  height: 100vh;
}
</style>