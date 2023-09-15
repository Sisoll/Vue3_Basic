<!--
:key  綁定 key 屬性
@keyframes
-->

<script setup>


import {ref} from "vue";

const testKey = ref('hello')

setTimeout(() => {
  testKey.value = 'world'
} , 1500)



defineProps({
  msg: String,
})

</script>

<template>

  <h1>{{msg}}</h1>

<!-- 綁定key，類似if的狀況，會整個刪掉重新建立dom-->
  <p class="render"  :key="testKey">
    {{testKey}}
  </p>

  <!--  如果不加key不會影響到父層，就只是替換文字-->
  <p class="render">
    {{testKey}}
  </p>


</template>

<style>
.render{
  font-size: 30px;
  animation:openIn 1s ease-in-out ;
}

@keyframes openIn {
  0% {
    opacity: 0;
    transform: translateY(30px);
  }
  100%{
    opacity: 1;
    transform: translateY(0);
  }
}

</style>



