# Vue.jsの基礎

## テンプレート構文
templateタグはhtmlをそのまま渡されるわけではない。ViteによってJavaScriptのコードに変換される。templateのなかのテンプレート構文はhtmlの文法に独自のルールを追加している。

## 二重波括弧の使い方
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
```
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

