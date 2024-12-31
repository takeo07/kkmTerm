<script setup lang="ts">
import { onMounted } from 'vue';
import { Terminal } from '@xterm/xterm';
import '@xterm/xterm/css/xterm.css';

onMounted(() => {
  console.log('onMounted');
  let term = new Terminal();
  term.open(document.getElementById('terminal')!);
})
</script>

<template>
  <div id="terminal"></div>
</template>

<style scoped>
</style>
<style>

</style>