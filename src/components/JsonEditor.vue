<template>
  <div class="editor" ref="dom"></div>
</template>

<script setup>
import { onMounted, defineProps, defineEmits, ref } from 'vue';
import * as monaco from 'monaco-editor';

import EditorWorker from 'monaco-editor/esm/vs/editor/editor.worker?worker';
import HtmlWorker from 'monaco-editor/esm/vs/language/html/html.worker?worker';

self.MonacoEnvironment = {
  getWorker(workerId, label) {
    if (label === 'html') {
      return new HtmlWorker();
    }
    return new EditorWorker();
  },
};

const props = defineProps({
  modelValue: String,
});

const emit = defineEmits(['update:modelValue']);

const dom = ref();

let instance;

onMounted(() => {
  const htmlModel = monaco.editor.createModel(props.modelValue, 'html');

  instance = monaco.editor.create(dom.value, {
    model: htmlModel,
    tabSize: 4,
    automaticLayout: true,
    scrollBeyondLastLine: false,
    theme: 'vs-dark',
    minimap: { // 关闭小地图
      enabled: false,
    },
    fontSize:16
  });

  instance.onDidChangeModelContent(() => {
    const value = instance.getValue();
    emit('update:modelValue', value);
  });
});
</script>

<style scoped>
.editor {
  height: 100%;
}
</style>