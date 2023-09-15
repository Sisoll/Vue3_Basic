<!--
監聽器

  watch (XXX , (new , old) => {})  => 只能監聽第一層的變化
  watch (XXX , (new , old) => {} , deep:true)  => 可以監聽到物件內的變化，但因為是用遞迴去做，效能會較差
    => 如果要同時監聽多個 XXX 可以放陣列。

  watchEffect( () => {XXXXXXXX} )  => 只要 {} 內有用到的參數有變化都會觸發，不需要指定監聽內容。

  停止方式: 設定回傳值 & stop()  ????

@ = v-on
將值傳回父組件

-->

<script setup>

import {reactive, ref} from "vue";
import {watch} from "vue";
import {watchEffect} from "vue";
import  ComponentF_child from './ComponentF_child.vue'

// watch
const watchText = ref({
  levels:{
    text:'',
  },
  label:'0',
})

watch(
    [() => watchText.value.levels.text , () => watchText.value.label],
    (newStr , oldStr) => {
      console.log(newStr,oldStr)}
)

// watchEffect
const watchEffectText = ref(1)
watchEffect(   // 不需要寫監聽那些~而是effect裡面只要有值被變化就會反應
    ()=>{
      console.log(watchEffectText.value)
    }
)

// stop
const stopWatch = ref('')

const stop = watchEffect(
    ()=> {
      console.log(stopWatch.value)
      if (stopWatch.value === 'stop') stop()
    })

//  usage
const example = ref('')
const dynamicStyle = reactive({
  transition: 'ease-in-out 0.4s',
})

watch(example , ()=>
    {
      if(example.value.length % 2 === 0){
        dynamicStyle.color = 'blue'
        dynamicStyle.fontSize = '14px'
      }
      else {
        dynamicStyle.color = 'red'
        dynamicStyle.fontSize = '24px'
      }
    })

//
const transText = ref('')

const handleUpdate = (data)=>{
  console.log(data)
}


//
defineProps({
  msg: String,
})

</script>

<template>
  <h1>{{msg}}</h1>
  <!--  watch -->
  <div>
    <p> ----  watch  ----</p>
    <input type="text" v-model="watchText.levels.text">
    <input type="text" v-model="watchText.label">

  </div>
  <!--  watchEffect  -->
  <div>
    <p> ---- watchEffect ---- </p>
    <input type="number" v-model="watchEffectText">
    <!--  watchEffect with Stop -->
  </div>
  <!--  stop Watch  -->
  <div>
      <p> ---- stop watch ---- </p>
      <input type="text" v-model="stopWatch">
  </div>
  <!--usage 1-->
  <div>
    <p>實例</p>
    <input type="text" v-model="example" :style="dynamicStyle">
  </div>
  <!--usage 2-->

  <div>
    <p>取得子組件傳回的值</p>
    <input type="text" v-model="transText">
    <br>
    <ComponentF_child :data="transText"  @update = "handleUpdate"/>   <!-- 將transText bind 到 Child的data -->
  </div>
</template>



<style>
</style>



