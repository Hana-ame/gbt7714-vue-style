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

  const reWrap:RegExp = /@(\w+)\{((?:.|\s)*)\}/
  const arr = reWrap.exec(input.value)

  console.log(arr)

  if (arr === null){
    return { input }
  }
  const type = arr[1]
  const params = arr[2]

  let reParams = /\s*((?:.)*?)={((?:.)*)}/g

  // const paramArr = reParams.exec(params)
  
  console.log("reParams.exec(params)")
  for (let i=0; i<20; i++) {
    console.log(reParams)
    const m = reParams.exec(params);
    console.log(reParams)
    if (m) {
      console.log(m[1],m[2])
    } else {
      break
    }
  }

  return {
    "input": input,
    "arr": arr,
    "type": type,
    "params": params,
    // "paramArr": paramArr,
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
