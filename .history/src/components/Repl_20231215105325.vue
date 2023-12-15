<script setup>
import { ref, watchEffect } from "vue";
import { Repl, ReplStore } from "@vue/repl";
import Monaco from "@vue/repl/monaco-editor";
import "@vue/repl/style.css";
import welcomeCode from "./Cesium.vue?raw"
import {headHTML} from './datas.ts'

const store = new ReplStore();

watchEffect(() => history.replaceState({}, "", store.serialize()));


// const files = {
//         ["App.vue"]: new File("src/App.vue", welcomeCode)
//       }

const defaultfiles = store.getFiles()

const files = {}
Object.keys(defaultfiles).forEach(keys => {
  files[key] = 
})

files["App.vue"] = new File("App.vue", welcomeCode)

// store.setFiles(files)
//     state.activeFile = state.files['App.vue'];
</script>

<template>
  <Repl
    :editor="Monaco"
    :store="store"
    :clear-console="false"
    :preview-options="{
      headHTML,
    }"
  />
</template>

<style>
.vue-repl {
  height: 700px !important;
}
</style>
