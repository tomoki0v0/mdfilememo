# レンダリング

[vue.jsにもどる](../vuejs.md)

### v-if, v-else, v-else-if
```vue
<script setup>
import { ref } from 'vue'
const ok = ref(true)
const maybeOk = ref(true)
</script>
<template>
  <button @click="ok = !ok">toggle</button>
  <p v-if="ok">OK!</p>
  <p v-else-if="maybeOk">maybe OK!</p>
  <p v-else>not OK...</p>
</template>
```
`v-if`、`v-else-if`、`v-else`が入っているタグは連続させなければならない

### templateタグを使用して複数の要素にv-ifを適用