<script setup>
//defineProps()不用import
//定義動態傳值的參數及type
const props = defineProps({
  msg: String
})
</script>
<template>
  <!-- ChildComp.vue -->
  <h2>{{ msg || 'No props passed yet' }}</h2>
</template>
<style></style>
