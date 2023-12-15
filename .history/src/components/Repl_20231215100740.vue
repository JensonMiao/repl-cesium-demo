<script setup>
import { ref, watchEffect } from "vue";
import { Repl, ReplStore } from "@vue/repl";
import Monaco from "@vue/repl/monaco-editor";
import "@vue/repl/style.css";
import { headHTML } from "./datas";

const store = new ReplStore();

watchEffect(() => history.replaceState({}, "", store.serialize()));

const customImportStatements = ref([]);
const customAppUsageCodes = ref([]);
</script>

<template>
  <Repl
    :editor="Monaco"
    :store="store"
    :clear-console="false"
    :preview-options="{
      headHTML,
      customCode: {
        importCode: customImportStatements,
        useCode: customAppUsageCodes,
      },
    }"
  />
</template>

<style>
.vue-repl {
  height: 700px !important;
}
</style>
