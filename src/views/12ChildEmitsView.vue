<script setup>
// 宣告觸發的事件
const emit = defineEmits(['response'])
// 帶參數觸發
emit('response', 'hello from child')
</script>

<template>
  <h2>Child component</h2>
</template>
