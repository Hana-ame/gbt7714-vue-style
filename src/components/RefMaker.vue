<script setup lang="ts">
import { ref, computed, reactive } from 'vue'
import { NInput }  from 'naive-ui'

// defineProps<{ msg: string }>()

const input = ref("all")

let arr = [1,2,3]
const arrr = ref([1,2,3])
const arrrr = reactive([1,2,3])

console.log(arr,arrr,arrrr)

const result = computed({
  get() {
    arr.push(arr[arr.length-3])
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
    <hr />
    {{ arr }}
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
