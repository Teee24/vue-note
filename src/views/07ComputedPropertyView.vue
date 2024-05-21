<script setup>
import { ref, computed } from 'vue'

let id = 0

const newTodo = ref('')
const hideCompleted = ref('')
const todos = ref([
  { id: id++, text: 'Learn HTML', done: true },
  { id: id++, text: 'Learn JavaScript', done: true },
  { id: id++, text: 'Learn Vue', done: false }
])
const filteredTodos = computed(() => {
  // 計算屬性 預設是唯讀

  //利用hideComplete.value去控制todo是否顯示已完成事項
  return hideCompleted.value ? todos.value.filter((t) => !t.done) : todos.value
})

function addTodo() {
  //新增一個done的布林值變數去綁定checkbox的屬性
  todos.value.push({ id: id++, text: newTodo.value, done: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}

const firstName = ref('')
const lastName = ref('')
const fullName = computed({
  // getter
  get() {
    return firstName.value + ' · ' + lastName.value
  },
  // setter
  set(newValue) {
    // 注意：我们这里使用的是解构赋值语法
    //[firstName.value, lastName.value] = newValue.split(' ')

    const parts = newValue.split(' ')
    firstName.value = parts[0]
    lastName.value = parts[1]
  }
})
function onInput(e) {
  firstName.value = e.target.value
}
function Input(e) {
  lastName.value = e.target.value
}
</script>

<template>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" required placeholder="new todo" />
    <button>Add Todo</button>
  </form>
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done" />
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>

  <!-- 計算屬性緩存vs 方法 -->
  <!-- 在結果上確實是完全相同的 -->
  <!-- 不同之處在於計算屬性值會基於其響應式依賴被緩存 -->
  <br />
  <hr />
  <h2>可寫入計算屬性|Writable Computed</h2>
  <input type="text" @input="onInput" :value="firstName" placeholder="firstName..." />
  <input type="text" @input="Input" :value="lastName" placeholder="lastName..." />
  <p>{{ fullName }}</p>
</template>

<style>
.done {
  text-decoration: line-through;
}
</style>
