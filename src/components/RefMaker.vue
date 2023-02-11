<script setup lang="ts">
import { ref } from 'vue'
import { NInput }  from 'naive-ui'

// defineProps<{ msg: string }>()

const count = ref(0)

const value = ref("")

</script>

<template>
    <n-input
      v-model:value="value"
      type="textarea"
    />
    {{ value }}
</template>

<style>
  n-input {
    width: 100%;
  }
</style>
