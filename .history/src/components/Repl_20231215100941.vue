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
const welcomeCode = `\
<script setup lang='ts'>
import { ref } from 'vue'
import { Button } from 'vant';
import { injectVant } from './vant-inject-plugin.js'
injectVant()
const msg = ref('Hello Vant!')
</script>
<template>
  Button：
  <Button type="primary">{{ msg }}</Button>
  <van-divider />
  van-button：
  <van-button type="primary">{{ msg }}</van-button>
  <van-divider />
  van-Button：
  <van-Button type="primary">{{ msg }}</van-Button>
</template>
`

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
