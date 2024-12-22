<script setup lang="ts">
import {onMounted} from 'vue';
import {Terminal} from '@xterm/xterm';
import '@xterm/xterm/css/xterm.css';

onMounted(() => {
    console.log('onMounted');
    const elem = document.getElementById('terminal')!;
    var term = new Terminal();
    term.open(elem);
})
</script>

<template>
    <div id="terminal"></div>
</template>

<style scoped>

</style>
<style>

</style>