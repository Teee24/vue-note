<script setup>
import { ref, onMounted } from 'vue'

//這個ref 使用null值來初始化
const pElementRef = ref(null)
onMounted(() => {
  // 此时组件已经挂载。
  pElementRef.value.textContent = 'mounted!'
})
</script>
<template>
  <p ref="pElementRef">Hello</p>
</template>
<style></style>
