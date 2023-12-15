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

<script setup lang="ts">
import { onMounted } from "vue";

const Cesium = (window as any).Cesium
Cesium.Ion.defaultAccessToken =
"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI1NzNiNGRmNS05YWRkLTQ3NTQtOGNiOS1mM2U4ZTk5YmYyMjQiLCJpZCI6MTgwNDU5LCJpYXQiOjE3MDA4MTc2MDZ9.557T1vCfCf2p2fhP3ulyaQ_4ZQ4e8Zfhr6MQKYULF3o";

onMounted(() => {
new Cesium.Viewer("cesiumContainer");
});
</script>

<template>
  <div id="cesiumContainer" />
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
