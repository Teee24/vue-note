<script setup>
import { ref } from 'vue'
const text = ref('')
const showClass = ref('show')
function onInput(e) {
  //v-on 处理函数会接收原生 DOM 事件
  //監聽事件的目標值
  text.value = e.target.value
}
</script>
<template>
  <!-- 在表單的輸入元素上建立雙向綁定|v-bind、v-on -->
  <!--  :value="text"是語法糖 -->
  <input :value="text" @input="onInput" placeholder="Type here..." />
  <p>{{ text }}</p>
  <input v-model="text" @input="onInput" />
  <p :class="showClass">{{ text }}</p>
</template>
<style>
.show {
  font: bold;
  font-size: larger;
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  color: cadetblue;
}
</style>
