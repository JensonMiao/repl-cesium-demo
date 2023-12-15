<script setup>
import { ref, watchEffect } from "vue";
import { Repl, ReplStore } from "@vue/repl";
import Monaco from "@vue/repl/monaco-editor";
import "@vue/repl/style.css";
import welcomeCode from "./Cesium.vue?raw"

const store = new ReplStore();

watchEffect(() => history.replaceState({}, "", store.serialize()));

// const files = {
//         ["src/App.vue"]: new File("src/App.vue", welcomeCode)
//       }

      

</script>

<template>
  <Repl
    :editor="Monaco"
    :store="store"
    :clear-console="false"
  />
</template>

<style>
.vue-repl {
  height: 700px !important;
}
</style>
