<script setup lang="ts">
import { ref, computed, reactive } from 'vue'
import { NInput }  from 'naive-ui'

// defineProps<{ msg: string }>()

const input = ref("all")

// let arr = [1,2,3]
// const arrr = ref([1,2,3])
// const arrrr = reactive([1,2,3])

// console.log(arr,arrr,arrrr)

// 监视某个变量改动？
const obj = computed(() => {
  // console.log(this)
  console.log("obj", obj)
  console.log(input)

  const reWrap:RegExp = /@(\w+)\{((.|)*)\}/
  const arr = reWrap.exec(input.value)

  console.log(arr)
  

  return {
    "input": input,
    "arr": arr,
  }
})

const result = computed<string>({
  get() {
    // arr.push(arr[arr.length-3])
    // console.log('get')
    // return obj.input.value
    return "getter"
  },
  set(newValue: any) {
    // console.log(result)
    // input.value = newValue
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
    {{ obj }}
    <hr />
    {{ result }}
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
