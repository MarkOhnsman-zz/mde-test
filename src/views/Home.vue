<template>
  <div>
    <h1>Toast-Ui/Vue-Editor</h1>
    <a href="https://github.com/nhn/tui.editor/tree/master/apps/vue-editor">Source Here</a>
    <editor ref="toastuiEditor" initialEditType="wysiwyg" />
    <button @click="getHtml">Get HTML (see console)</button>
    <button @click="getMD">Get Markdown (see console)</button>
    <h3>MD Viewer</h3>
    <viewer
      style="border: 1px solid black; padding: 1em;"
      ref="toastuiEditor2"
      :initialValue="preview"
    />
  </div>
</template>
<script>
import 'codemirror/lib/codemirror.css';
import '@toast-ui/editor/dist/toastui-editor.css';
import '@toast-ui/editor/dist/toastui-editor-viewer.css';

import { Viewer } from '@toast-ui/vue-editor';
import { Editor } from '@toast-ui/vue-editor';

export default {
  data() {
    return {
      editorOptions: {
        toolBarItems: []
      },
      preview: 'Use this to ***Render*** the Markdown'
    }
  },
  components: {
    Editor,
    Viewer
  },
  methods: {
    getHtml() {
      let html = this.$refs.toastuiEditor.invoke('getHtml');
      console.log(html)
    },
    getMD() {
      let md = this.$refs.toastuiEditor.invoke('getMarkdown');
      console.log(md)
    }
  }
};
</script>