<template>
  <Repl></Repl>
  <Cesium></Cesium>  
</template>
<script lang="ts" setup name="">
import Cesium from './components/Cesium.vue'
import Repl from './components/Repl.vue'

</script>
<style >
body{
  margin:0;
}
#app{
  height: 100vh;
  width:100vw;
}

</style>
