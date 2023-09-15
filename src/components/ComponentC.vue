<!--
 v-for 迴圈渲染與 key 屬性
 : 為v-bind的縮寫

-->

<script setup>

const stringList = [
    'string1',
    'string2',
    'string3'
]

const objectList = {
  'keyA': 'aa',
  'keyB': 'bb',
  'keyC': 'cc'
}

defineProps({
  msg: String,
})

</script>

<template>

  <h1>{{msg}}</h1>

  <h3>字串的list</h3>
  <p v-for="str  in stringList">
    {{str}}
  </p>

  <h3>物件的list</h3>
  <p v-for="obj  in objectList">
    {{obj}}
  </p>
  <h3>物件的取出依序 (value / key / index) </h3>
  <p v-for="(value,key,index)  in objectList">
    {{key}} -- {{value}}  -- {{index}}
  </p>

  <hr/>

</template>

<style>

</style>



