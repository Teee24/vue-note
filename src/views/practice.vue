<script setup>
import { ref, computed } from 'vue'

const x = ref(1)
const y = ref(2)
const z = ref(0)
// const z = computed(() => x.value * y.value)->這個效能比較下面的好
z.value = x.value * y.value
const addY = () => {
  y.value++
  z.value = x.value * y.value
}

// :class指令也可以和一般的classattribute 共存
const isActive = ref(true)
const hasError = ref(true)
const activeClass = ref('active')
const errorClass = ref('text-danger')
const activeColor = ref('red')
const fontSize = ref(30)

const styleObject = ref({
  color: 'red',
  fontSize: '30px'
})
const overridingStyles = ref({
  'background-color': 'yellow'
})
const ok = ref(true)
const parentMessage = ref('Parent')
const items = ref([{ message: 'Foo' }, { message: 'Bar' }])
const myObject = ref({
  title: 'How to do lists in Vue',
  author: 'Jane Doe',
  publishedAt: '2016-04-10'
})
const count = ref(0)
const name = ref('Vue.js')

function greet(event) {
  alert(`Hello ${name.value}!`)
  alert(event.currentTarget)
  // `event` 是 DOM 原生事件
  if (event) {
    //e.target：指的是觸發事件的物件。
    // e.currentTarget：指的是被監聽的物件。
    alert(event.target.tagName)
    alert(event.currentTarget.tagName)
  }
}
function warn(message, event) {
  // 这里可以访问原生事件
  if (event) {
    event.preventDefault()
  }
  alert(message)
}
function onClick() {
  alert('阻止提交表單~')
}
function submit() {
  alert('OK')
}
function onPageDown() {
  alert('change')
}
const age = ref(22)
const toggle = ref(true)
</script>
<template>
  <div class="static" :class="{ active: isActive, 'text-danger': hasError }">12345</div>
  <div class="static active">1235545</div>
  <div :class="[activeClass, errorClass]">綁定數組</div>
  <div :style="{ color: activeColor, fontSize: fontSize + 'px' }">綁定內聯樣式-綁定物件</div>
  <div :style="styleObject">綁定內聯樣式-直接綁定一個樣式物件</div>
  <div :style="[styleObject, overridingStyles]">綁定內聯樣式-綁定數組</div>
  <div :style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }">樣式多值</div>
  <!-- v-show僅切換了該元素上名為display的CSS 屬性 -->
  <h1 v-show="ok">Hello!</h1>
  <h2>清單渲染</h2>
  <!-- <div v-for="item of items"></div> -->
  <ul>
    <li v-for="{ message } in items">
      {{ message }}
    </li>
  </ul>

  <!-- 有 index 索引时 -->
  <ul>
    <li v-for="({ message }, index) in items">{{ message }}: {{ index }}</li>
  </ul>

  <h2>v-for與物件</h2>
  <!-- 使用情境:index+1可以當排序的編號key可以用在Table的欄位名稱，value為資料 -->
  <ul>
    <li v-for="(value, key, index) in myObject">{{ index }}. {{ key }}: {{ value }}</li>
  </ul>
  <h2>template上的v-for</h2>
  <ul>
    <template v-for="item in items">
      <li>{{ item.message }}</li>
      <li class="divider" role="presentation">----</li>
    </template>
  </ul>
  <h2>計算屬性與方法</h2>
  <!-- computed要放響應式變數才會跟著作用 -->
  <h2>事件處理</h2>
  <!-- 內嵌事件處理器 -->
  <button @click="count++">Add 1</button>
  <p>Count is: {{ count }}</p>
  <hr />
  <!-- 方法事件處理器 -->
  <!-- `greet` 是上面定义过的方法名 -->
  <button @click="greet">Greet</button>
  <h2>在內聯事件處理器中存取事件參數</h2>
  <!-- 使用特殊的 $event 变量 -->
  <button @click="warn('Form cannot be submitted yet.', $event)">Submit</button>

  <!-- 使用内联箭头函数 -->
  <button @click="(event) => warn('Form cannot be submitted yet.', event)">Submit</button>
  <h3>事件修飾符</h3>
  <!-- event.stopPropagation() -->
  <form @submit.prevent><button type="submit" @click="onClick">submit</button></form>
  <!-- 按鍵修飾符 -->

  <!-- 仅在 `key` 为 `Enter` 时调用 `submit` -->
  <input @keyup.enter="submit" />
  <input @keyup.page-down="onPageDown" />
  <!-- 僅會在$event.key為'PageDown'時呼叫事件處理 -->
  <h3>.exact修飾符</h3>
  <!-- .exact修飾符允許精確控制觸發事件所需的系統修飾符的組合。 -->
  <!-- 当按下 Ctrl 时，即使同时按下 Alt 或 Shift 也会触发 -->
  <button @click.ctrl="onClick">A</button>

  <!-- 仅当按下 Ctrl 且未按任何其他键时才会触发 -->
  <button @click.ctrl.exact="onCtrlClick">A</button>

  <!-- 仅当没有按下任何系统按键时触发 -->
  <button @click.exact="onClick">A</button>
  <h3>滑鼠按鍵修飾符</h3>
  <button @click.right="onClick">右鍵點擊</button>
  <!-- 表單輸入綁定 -->
  <h4>true-value和false-value是Vue 特有的attributes，僅支援和v-model配套使用</h4>
  <input type="checkbox" v-model="toggle" true-value="yes" false-value="no" />
  <label for="toggle">{{ toggle }}</label>
  <select v-model="selected">
    <!-- 内联对象字面量 -->
    <option :value="{ number: 123 }">123</option>
  </select>
  <!-- v-model.lazy在 "change" 事件后同步更新而不是 "input" -->
  <input v-model.number="age" />
  <h4>
    模板引用-例如在元件掛載時將焦點設定到一個input 元素上，或在一個元素上初始化一個第三方函式庫。
  </h4>
</template>
<style></style>
