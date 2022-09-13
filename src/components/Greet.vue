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
  <h2>v1.5.0</h2>
  <p>{{ greetMsg }}</p>
</template>
