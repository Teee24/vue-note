<script setup>
import { ref } from 'vue'

const titleClass = ref('title')
//ref吃下面style綁定的title，再利用titleClass給到html上的attribute綁定
</script>

<template>
  <h1 v-bind:class="titleClass">(全寫)Make me red</h1>
  <h1 :class="titleClass">(簡寫)Make me red</h1>
</template>

<style>
.title {
  color: red;
}
</style>
