<template>
  <div>
    <h1>{{ msg }}</h1>
    <div > Count is: {{ count }} </div>
    <el-button @click="count++">Add 1</el-button>
    <el-button @click="backendAdd">Add 2 in backend</el-button>
  </div>
</template>

<script setup lang="ts">
import { invoke } from '@tauri-apps/api/tauri'
defineProps<{ msg: string }>()

const count = ref(0)
async function backendAdd() {
  count.value = await invoke('backend_add', { number: count.value })
}
</script>
