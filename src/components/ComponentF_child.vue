<!--
父子層之間的資料傳遞
  從父那邊拿資料
   defineProps (XXX)  => XXX可以用[]或是{}，{}上比較靈活
  傳資料到父
  defineEmits()  => 定義事件(動作)，然後發送到父

-->

<script setup>
import {computed, watch} from "vue";

// defineProps(['data'])

const props = defineProps({
  data:{
    type: String,
    default: '',
  },
})

const countWords = computed(
    ()=>{
      return props.data.length
    })

const emit = defineEmits(['update'])

watch(countWords , (newCount) =>{
  emit('update' , newCount)  // 可以多個參數回傳
})

</script>


<template>
  <p>字數:{{countWords}}</p>

</template>



<style>
</style>



