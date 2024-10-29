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



<!--
# 코드 설명

1. 템플릿(Template) 구조
- <div>로 전체 컴포넌트를 감싸고 있음
- <h1> 태그로 제목을 표시
- <img> 태그에 v-bind 디렉티브(:src)를 사용하여 이미지 소스를 바인딩

2. 스크립트 구조
- <script setup>: Vue 3의 Composition API를 사용하기 위한 구문
- import { ref }: Vue의 반응형 참조를 생성하기 위한 ref 함수를 가져옴
- const imgSrc = ref(): 이미지 URL을 반응형 데이터로 선언

3. 주요 특징
- v-bind(:) 사용으로 반응형 데이터가 변경될 때마다 이미지가 자동으로 업데이트됨
- ref()로 생성된 반응형 변수는 컴포넌트 내에서 .value로 접근 가능
- 템플릿에서는 자동으로 .value가 unwrap되어 직접 사용 가능

4. 데이터 흐름
- imgSrc 변수의 값이 변경되면 Vue의 반응형 시스템이 감지
- 감지된 변경사항이 템플릿의 img 태그에 자동으로 반영
- 이를 통해 동적인 이미지 교체 가능

5. Composition API 특징
- setup 키워드로 컴포지션 API 사용
- 컴포넌트 로직을 더 유연하게 구성 가능
- 타입스크립트와의 호환성이 좋음
-->

