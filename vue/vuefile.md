# Vueファイル

### 基本構成
```
<script>JavaScriptについて</script>
<template>htmlファイルの記述</template>
<style>cssの記述</style>
```

### ScriptとTemplateの連携

```vue:App.vue
<script setup>
const title = 'Vue.js Course'
</script>
<template>
  <h1>Title: {{ title }}</h1>
</template>
```

### リアクティビティ
```vue:App.vue
<script setup>
import { ref } from 'vue'
const title = 'Vue.js Course'
let price = ref(9.99) // refオブジェクトを作る
function increment() {
  price.value += 1;
}
</script>
<template>
  <h1>Title: {{ title }}</h1>
  <h2>Price: ${{ price - 1 }}</h2>
  <button @click="increment">button</button>
</template>
```
`ref(9.99)`のようにしてrefオブジェクトを作成し、javascript内では`price.value`のようにして値を扱う。template内では`.value`を付ける必要がない。

### オブジェクトをリアクティブに
```vue:App.vue
<script setup>
import { ref, reactive } from 'vue'
const title = 'Vue.js Course'
let price = ref(9.99) // refオブジェクトを作る
function increment() {
  price.value += 1;
  instructor.age += 1;
}
const instructor = reactive({
  name: 'Yoshipi',
  age: 25
})
console.log(instructor.age)
</script>
<template>
  <h1>Title: {{ title }}</h1>
  <h2>Price: ${{ price - 1 }}</h2>
  <button @click="increment">button</button>
  <h2>Instructor age: {{ instructor.age }}</h2>
</template>
```
`reactive()`を使用してオブジェクトをリアクティブにする。その時、`.value`が省略される。