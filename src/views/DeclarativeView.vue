<script setup>
import { ref } from 'vue'
import { reactive } from 'vue'

//import { reactive, ref } from 'vue' = import { ref } from 'vue'+import { reactive } from 'vue'

//使用ref()函數來宣告響應式狀態

//import { reactive } from 'vue' ，reactive只適用於物件(包括陣列和內建類型，如Map和Set)
//import { ref } from 'vue'，ref()則可以接受任何值類型，.value回傳物件

//元件模板中存取ref，請從元件的setup()函數中宣告並傳回它們
const message = ref('Hello ref!')
console.log(message.value)
message.value = 'Changed'

const counter = reactive({
  count: 0
})
console.log(counter.count) // 0
counter.count++
</script>

<template>
  <h1>{{ message }}</h1>
  <h2>{{ message.split('').reverse().join('') }}</h2>
  <p>Count is: {{ counter.count }}</p>
</template>

<style scoped></style>
