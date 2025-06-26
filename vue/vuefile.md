# Vueファイル

### 基本構成
```
<script>JavaScriptについて</script>
<template>htmlファイルの記述</template>
<style>cssの記述</style>
```

### ScriptとTemplateの連携

```javascript:App.vue
<script setup>
const title = 'Vue.js Course'
</script>
<template>
  <h1>Title: {{ title }}</h1>
</template>
```