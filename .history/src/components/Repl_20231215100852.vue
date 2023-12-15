<script setup>
import { ref, watchEffect } from "vue";
import { Repl, ReplStore } from "@vue/repl";
import Monaco from "@vue/repl/monaco-editor";
import "@vue/repl/style.css";

const store = new ReplStore();

watchEffect(() => history.replaceState({}, "", store.serialize()));

const headHTML = ref([`
    <script type="text/javascript" src="./cesium/Cesium.js"></script>
    <link rel="stylesheet" href="./cesium/Widgets/widgets.css"></link>
`]);
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
