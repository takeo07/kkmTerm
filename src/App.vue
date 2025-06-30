<script setup lang="ts">
import { onMounted } from 'vue';
import { Terminal } from '@xterm/xterm';
import '@xterm/xterm/css/xterm.css';
import { spawn } from 'tauri-pty';
import 'vuetify/styles';

onMounted(() => {
  const terminal = new Terminal({
    cols: 80,
    rows: 30,
    theme: {
      background: '#1e1e1e',
      foreground: '#ffffff',
    },
  });
  terminal.open(document.getElementById("terminal")!);
  const pty =spawn("bash", [], {
      cols: 80,
      rows: 30,
  });
  pty.onData((data) => {
    terminal?.write(data);
  });
  terminal.onData((data) => {
    pty.write(data);
  });
});

</script>

<template>
  <v-app>
    <v-system-bar color="secondary">
      System Bar
    </v-system-bar>

    <v-app-bar color="primary">
      <v-app-bar-title>
        Application Bar
      </v-app-bar-title>
    </v-app-bar>

    <v-navigation-drawer permanent>
      Navigation Drawer
    </v-navigation-drawer>

    <v-main>
      <v-container>
        <div id="terminal"></div>
      </v-container>
    </v-main>

    <v-bottom-navigation>
      Button Navigation
    </v-bottom-navigation>

    <v-footer color="primary" app>
      Footer
    </v-footer>

  </v-app>
</template>


<style scoped>

</style>
<style>

</style>