# Vue.jsの基礎

[vue.jsにもどる](../vuejs.md)

### テンプレート構文
templateタグはhtmlをそのまま渡されるわけではない。ViteによってJavaScriptのコードに変換される。templateのなかのテンプレート構文はhtmlの文法に独自のルールを追加している。

### 二重波括弧の使い方
二重波括弧の中身は単一式のみ
scriptの中でトップレベルで定義されている

## v-から始まるディレクティブ
```vue
<template>
  <div>{{ count }}</div>
  <div v-text="count"></div>
</template>
```
このようにディレクティブは書ける

### v-htmlを使ってデータをHTMLとして出力
```
<script setup>
import { ref } from 'vue'
const message = ref('<h1>Hello</h1>')
</script>
<template>
  <div v-html="message"></div>
</template>
```
htmlとして認識させることが出来る。ただしセキュリティに問題がある。信頼できるデータのみを変数に適用する。

### v-bindを使って属性値を指定する
```vue
<script setup>
import { ref } from 'vue'
const vueURL = ref('https://vuejs.org')
const vueId = ref('vue-link')
</script>
<template>
  <a :id="vueId" :href="vueURL">Vue.js</a>
</template>
```
v-bindディレクティブを使って属性値を指定する。省略して`:`のみで書く。v-bindと属性値が同じ場合には属性値を省略することが出来る。`:id="id"`→`:id`

### Boolean属性に対してv-bindを利用する方法
```vue
<button :disabled="false"></button>
```
boolean属性に対応しているものはfalseなどでできなくなる

### v-bindで1度に複数の属性を指定する方法
```vue
<a v-bind="{ id: vueId, href: vueURL }">
```
複数の属性にv-bindを指定する

### v-onを用いてクリックなどのイベント発生時に特定の処理を行う
```
<script setup>
import { ref } from 'vue'
const count = ref(0)
</script>
<template>
  <p>{{ count }}</p>
  <button v-on:click="count++"></button>
</template>
```
`v-on:`→`@`に省略
直接書くインラインハンドラと関数を書くメソッドハンドラに分けられる。

### v-onでイベント情報を取得する方法
```vue
<script setup>
import { ref } from 'vue'
const count = ref(0)
function countUp(event) {
  console.log(event)
  count.value++
}
</script>
<template>
  <p>{{ count }}</p>
  <button @click="count++"></button>
  <button @click="countUp"></button>
</template>
```
引数の中にeventの情報が入っている

### v-onでハンドラーに引数を渡す方法
```
<script setup>
import { ref } from 'vue'
const count = ref(0)
function countUp(event, times) {
  count.value = event.clientX * times
}
</script>
<template>
  <p>{{ count }}</p>
  <button @click="count++"></button>
  <button @click="countUp($event, 5)"></button>
</template>
```
引数がない場合は明示的にeventが引数に入力されるが、引数を準備する場合は明示的に`$event`を使って第一引数をeventにする。

### イベント修飾子
```vue
<a href="https://vuejs.org" @click="$event.preventDefault()">Vue.js</a>
```
`$event.preventDefault`でデフォルトの挙動を防ぎ、リンクが反応しなくなる。

```vue
<button @click="$event.stopPropagation()">button</button>
```
親の要素を伝播しない。

二つは以下の省略記法がある
```vue
<a href="https://vuejs.org" @click.prevent="">Vue.js</a>
<button @click.stop="">button</button>
```

### キー修飾子
```vue
<input type="text" @keyup.space.delete="count++" />
```
特定のキーに対して修飾子を付ける

### 各括弧を使ってディレクティブの引数にscriptのデータを指定
```vue
<script setup>
import { ref } from 'vue'
const count = ref(0)
const eventName = 'keyup'
</script>
<template>
  <p>{{ count }}</p>
  <input type="text" @[eventName].space.delete="count++" />
</template>
```

### v-modelを使用してinputを扱う
```vue
<script setup>
import { ref } from 'vue'
const userInput = ref('')
</script>
<template>
  <input v-model="userInput" type="text">
</template>
```
v-modelに指定することでuserInputが同期する。

### computedを使う
reactiveを保ったまま
```vue
<script setup>
import { ref, computed } from 'vue'
const score = ref(0)
const evaluation = computed(() => {
  return score.value > 3 ? 'Good' : 'Bad'
})
</script>
<template>
  <p>{{ score > 3 ? 'Good' : 'Bad' }}</p>
  <p>{{ evaluation }}</p>
  <p>{{ score }}</p>
</template>
```
computedを使えば処理もリアクティブの変数として格納できる。computed内で宣言されているものを実行する。

### class属性
```vue
<script setup>
import { ref } from 'vue'
</script>
<template>
  <div :class="{red: true, 'bg-blue': true}">Hello</div>
</template>
<style>
.red {
  color: red;
}
.bg-blue{
  background-color: blue;
}
</style>
```
class属性の中でtrueの値が適用される

### style属性
```vue
<script setup>
import { ref } from 'vue'
</script>
<template>
  <div :style="{color: 'red', 'background-color': 'blue'}">Hello</div>
</template>
```
v-bind属性でオブジェクトで指定することができる。



