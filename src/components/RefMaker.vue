<script setup lang="ts">
import { ref } from 'vue'

// defineProps<{ msg: string }>()

const count = ref(0)

const value = ref("")

</script>

<template>
    {{ value }}
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
