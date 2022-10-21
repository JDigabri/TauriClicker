<script setup>
import { ref } from "vue";
import { invoke } from "@tauri-apps/api/tauri";

const greetMsg = ref("");
let name = ref("0");

async function greet() {
  // Learn more about Tauri commands at https://tauri.app/v1/guides/features/command
  greetMsg.value = await invoke("greet", { name: name.value });
  name = greetMsg;
}
</script>

<template>
  <div class="card">
    <button type="" @click="greet()">
        <img src="/tauri.svg" class="logo tauri" alt="Tauri logo" />
      </button>
  </div>
  <h1>{{ greetMsg }}</h1>
</template>

