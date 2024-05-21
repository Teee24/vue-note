<script setup>
import { ref } from 'vue'
//將子元件從跟目錄底下的vue檔匯出並命名為ChildCompent
import ChildCompent from './11ChildPropsView.vue'
const greeting = ref('Hello from parent')
</script>
<template>
  <!-- Parent -->
  <!-- 傳遞動態值，在父元件綁定並重新賦值 -->
  <ChildCompent :msg="greeting" />
</template>
<style></style>
