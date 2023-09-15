<!--
computed 計算屬性 => 類似function ，基本上資料預處理的過程

  function 是每次頁面有不同都會重新計算!
  computed 會是其依賴的變數有改變的時候才會重新計算
    => F12看兩者在console的差異

computed
  1.使用時須要小心side-effect，純計算並返回。
  2.得出的結果直接使用，不需要再做其他修改

將get return的內容放到set的參數裡面
computed({
  get(){
    return result
  },
  set(result){
    doSomeThing....
  }
})

-->

<script setup>

import {computed, ref} from "vue";

// usage 1
const num = ref(0)
const txt = ref('hello')

const checkNumByFunction = () => {
  console.log('change by Function')
  if (Number.isNaN(num.value * 100)) return num
  else return ` ${num.value * 100}% `
}

const checkNumByComputed = computed(() => {
  console.log('change by Computed')
  if (Number.isNaN(num.value * 100)) return num
  else return ` ${num.value * 100}% `
})

// usage 2

const firstName = ref('Sisol')
const lastName = ref('Hsieh')

const fullName = computed({
  get(){
    return `${firstName.value} ${lastName.value} `
  },
  set(newName){
    const [newFirstName , newLastName] = newName.split(' ')
    firstName.value = newFirstName
    lastName.value = newLastName
  }
})


// usege 3
const props = defineProps({
  msg: String,
})

</script>

<template>
  <h1>{{msg}}</h1>

  <div>
    <h3>check console.log</h3>
    <input type="number" v-model="num">
    <input type="text" v-model="txt" >

    <p>{{checkNumByFunction()}}</p>
    <p>{{checkNumByComputed}}</p>
  <hr>
  </div>
  <hr>
  <div>
    <h3> 其他狀況:需要side-effect的時候</h3>
    <input type="text" v-model="firstName">
    <input type="text" v-model="lastName">

    <p>{{fullName}}</p>
  </div>
  <hr>

<!--    usege 3-->
  <div>
    <h3>從父層vue取得的"computed 計算屬性 "來用</h3>
    <p> 總共字數有 {{props.msg.length}}</p>




  </div>




</template>

<style>


</style>



