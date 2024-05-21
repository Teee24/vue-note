<style></style>
<template>
  <div>
    <p>Computed Property: {{ computedProperty }}</p>
    <p>Method: {{ method() }}</p>
    <button @click="increment">Increment</button>
  </div>
  <div>
    <p>
      主要區別在於其執行方式和緩存行為; Computed
      properties會自動緩存結果，只有在依賴變化時才重新計算
      Methods則不具備緩存功能，每次調用時都會重新執行
    </p>
  </div>
  <div>
    <h3>example 02</h3>
    <p>(methods)Books: {{ calculateBooksMessage() }}</p>
    <p>(computed)Books: {{ calculateBooksMessage_computed }}</p>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const count = ref(0)

// 计算属性
const computedProperty = computed(() => {
  console.log('Computed property evaluated')
  return count.value * 2
})

// 方法
const method = () => {
  console.log('Method called')
  return count.value * 2
}

const increment = () => {
  count.value++
}

const books = ref(['Book 1', 'Book 2', 'Book 3'])
function calculateBooksMessage() {
  return books.value.length > 0 ? 'Yes' : 'No'
}
const calculateBooksMessage_computed = computed(() => {
  //利用hideComplete.value去控制todo是否顯示已完成事項
  return books.value.length > 0 ? 'Yes' : 'No'
})
</script>
