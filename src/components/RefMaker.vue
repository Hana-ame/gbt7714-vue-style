<script setup lang="ts">
import { ref, computed } from 'vue'
import { NInput }  from 'naive-ui'

// defineProps<{ msg: string }>()

const input = ref("all")

const result = computed({
  get() {
    // console.log('get')
    return input.value
  },
  set(newValue) {
    // console.log('set')
    input.value = newValue
  }
})

</script>

<template>
    <n-input
      v-model:value="input"
      type="textarea"
    />
    {{ input }}
    <n-input
      v-model:value="result"
      type="textarea"
    />
</template>

<style>
  n-input {
    width: 100%;
  }
</style>
