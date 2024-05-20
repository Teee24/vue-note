<script setup>
const msg = 'only for text'
const msgHtml = 'style="color: red"' //test1
const msgHtml_2 = '<span style="color: red">how to use</span>' //test2
const msgHtml_3 = 'style="color: red"' //test3
const isButtonDisabled = true
const objectOfAttrs = {
  id: 'container',
  class: 'wrapper',
  style: 'color:blue'
}
const number = 0
const ok = false
const message = '上海自來水來自海上'
const id = 5

// const date = '2024-05-20T12:00:00'

// function formatDate(dateTime) {
//   const dateObj = new Date(dateTime)
//   return dateObj.toLocaleString() // 將日期時間格式化為本地化字符串
// }
// function toTitleDate(dateTime) {
//   const dateObj = new Date(dateTime)
//   return dateObj.toDateString() // 將日期轉換為簡短的日期字符串作為標題
// }

const seen = true
function doSomething(number) {
  return number + 2
}
</script>

<template>
  <!-- Mustache{{}} -->

  <h2>文字插植:{{ msg }}</h2>
  <!-- Raw HTML | v-html-->

  <h2>用於html:<span v-html="msgHtml"></span></h2>

  <h2>用於html:<span v-html="msgHtml_2"></span></h2>

  <!-- Attribute 綁定 | v-bind/:-->

  <div v-bind:id="msgHtml_3">Attribute Binding</div>
  <div :id="msgHtml_3">簡寫Attribute Binding</div>

  <div v-bind:id>同名簡寫01</div>
  <div v-bind:id>同名簡寫02</div>

  <button :disabled="isButtonDisabled">Boolean Attributes</button>

  <div v-bind="objectOfAttrs">動態綁定多個值</div>
  <!-- 使用JavaScript 表達式 -->
  <p>{{ number + 1 }}</p>
  <p>{{ ok ? 'YES' : 'NO' }}</p>
  <p>{{ message.split('').reverse().join('') }}</p>
  <div :id="`list-${id}`">???</div>
  <!-- {{ if (ok) { return message } }} 這個不行要用三元表達是，下面的 -->
  <p>{{ ok ? 'YES' : message }}</p>

  <!-- 呼叫函數 -->
  <!-- <time :title="toTitleDate(date)" :datetime="date">
    {{ formatDate(date) }}
  </time> -->

  <!-- 指令Directives -->
  <!-- v-if -->
  <p v-if="seen">Now you see me</p>
  <!-- 參數Arguments -->
  <a v-bind:href="url"> ... </a>
  <!-- 简写  參數Arguments-->
  <a :href="url"> ... </a>
  <!-- v-on指令，它將監聽DOM 事件 -->
  <a v-on:click="doSomething"> Click </a>
  <!-- v-on指令，简写 -->
  <a @click="doSomething"> ... </a>
  <p>被影響的結果: {{ number }}</p>
  <!-- 動態參數 -->
  <a v-bind:[attributeName]="url"> ... </a>
  <!-- 简写 -->
  <a :[attributeName]="url"> ... </a>

  <a v-on:[eventName]="doSomething"> ... </a>
  <!-- 简写 -->
  <a @[eventName]="doSomething"> ... </a>

  <!-- 動態參數值的限制 -->
  <!-- 應是一個字串，或者是null。特殊值null意為明確移除該綁定。其他非字串的值會觸發警告 -->
  <!-- 動態參數語法的限制 -->
  <!-- 1. 空格和引號，在HTML attribute 名稱中都是不合法的 -->
  <!-- 2. 需要避免在名稱中使用大寫字母，因為瀏覽器會強制將其轉換為小寫 -->

  <!-- 修飾符Modifiers -->
  <!-- 以點開頭的特殊後綴，表示指令需要以一些特殊的方式被綁定EX: -->
  <form @submit.prevent="onSubmit">event.preventDefault()</form>
  <!-- .prevent修飾符會告知v-on指令對觸發的事件呼叫event.preventDefault() -->
</template>

<style scoped>
/* <style scoped>只有這邊可以用 */
</style>
