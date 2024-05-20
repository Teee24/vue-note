<script setup>
import { reactive, ref } from 'vue'
// 記得用ref、reactive才可以讓DOM即時更新
const count = ref(0)
const num = reactive({ count: 0 }) //要包成物件
function decrement() {
  //update notice:要用value才讀的到
  return count.value++
}
function add() {
  //update notice:要用物件才讀的到
  return num.count++
}
</script>
<template>
  <!-- 監聽DOM 事件 -->
  <button v-on:click="decrement">{{ count }}</button>
  <button v-on:click="add">{{ num.count }}</button>
</template>
<style></style>
