<template>
  <div id="cesiumContainer" />
</template>

<script setup lang="ts">
import { onMounted } from "vue";
Cesium.Ion.defaultAccessToken =
"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI1NzNiNGRmNS05YWRkLTQ3NTQtOGNiOS1mM2U4ZTk5YmYyMjQiLCJpZCI6MTgwNDU5LCJpYXQiOjE3MDA4MTc2MDZ9.557T1vCfCf2p2fhP3ulyaQ_4ZQ4e8Zfhr6MQKYULF3o";

onMounted(() => {
new Cesium.Viewer("cesiumContainer");
});
</script>
