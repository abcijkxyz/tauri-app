<script setup lang="ts">
import { ref } from 'vue';
import { invoke } from '@tauri-apps/api/tauri';

const greetMsg = ref('');
const name = ref('');

async function greet() {
  greetMsg.value = await invoke('greet', { name: name.value });
}
</script>

<template>
  <div class="card">
    <input id="greet-input" v-model="name" placeholder="Enter a name..." />
    <button type="button" @click="greet()">Greet</button>
  </div>
  <h1>v1.6.0</h1>
  <p>{{ greetMsg }}</p>
</template>
