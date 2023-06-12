<template>
  <div style="position: absolute;;inset: 0;display: flex;">
    <div class="container">
      <JsonEditor v-model="code"></JsonEditor>
    </div>
    <iframe :src="content"></iframe>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import JsonEditor from './components/JsonEditor.vue';

const code = ref(`<div style="height:100px;width:100px;background-color:rgb(200,200,200)">
    html
</div>`);

const content = computed(() => {
  //encodeURIComponent 字符串作为 URI 组件进行编码
  return `data:text/html;charset=utf-8,${encodeURIComponent(
    code.value
  )}`;
});
</script>

<style scoped>
.container {
  /* position: fixed; */
  height: 100%;
  width: 50%;
}

iframe {
  height: 100%;
  width: 50%;
}
</style>

