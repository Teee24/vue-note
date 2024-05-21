<script setup>
import { ref } from 'vue'
import ChildCop from './12ChildEmitsView.vue'

const childMsg = ref('No child msg yet')
</script>
<template>
  <!-- 從子元件動態事件綁定 -->
  <ChildCop @response="(msg) => (childMsg = msg)" />
  <p>{{ childMsg }}</p>
</template>
<style></style>
