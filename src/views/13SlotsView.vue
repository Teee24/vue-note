<script setup>
import { ref } from 'vue'
import ChildCom from './13ChildSlotsView.vue'
import ChildComp from './13CSlotsView.vue'

const msg = ref('from parent')
</script>
<template>
  <!-- 有給值就不不會顯示slot內容 -->
  <ChildCom> Message: {{ msg }}</ChildCom>
  <!-- 沒有給<ChildCom>傳遞任何插槽內容，所以你將看到預設內容 -->
  <ChildComp />
</template>
<style></style>
