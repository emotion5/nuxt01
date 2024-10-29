<template>
  <div>   
    <p>{{ message }}</p>    
  </div>
</template>

<script setup>
import { ref } from 'vue'
const message = ref('안녕하세요, 민!')
</script>


 
 <!--
 # 코드 설명
 
 1. 템플릿(Template) 구조
 - <div>로 컴포넌트의 최상위 요소를 정의
 - <p> 태그 안에 이중 중괄호 {{ }}를 사용하여 반응형 데이터 message를 표시
 - 이중 중괄호는 Vue의 텍스트 보간법(Text Interpolation)을 의미
 
 2. 스크립트 구조
 - <script setup>: Vue 3의 Composition API 사용을 위한 구문
 - import { ref }: Vue의 반응형 참조를 만드는 ref 함수 임포트
 - const message = ref('안녕하세요, 민!'): 문자열을 반응형 데이터로 선언
 
 3. 주요 기능
 - ref()로 생성된 반응형 변수는 .value로 값을 변경 가능
  예: message.value = '새로운 메시지'
 - 템플릿에서는 .value 없이 직접 사용 가능 (자동 unwrap)
 - message 값이 변경되면 화면이 자동으로 업데이트됨
 
 4. 데이터 바인딩
 - 단방향 데이터 바인딩의 예시
 - script의 데이터가 변경되면 템플릿에 자동 반영
 - 반응형 시스템을 통한 자동 UI 업데이트
 
 5. Composition API의 장점
 - 로직의 재사용성이 높음
 - 코드 구성이 더 유연함
 - TypeScript와의 호환성이 우수
 -->