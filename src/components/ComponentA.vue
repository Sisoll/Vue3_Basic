<!--
資料的單項及雙向綁定
{{}}
v-model
ref() => 如果是物件型態需要 .value 才能取出值，如果是基本型態可以直接用。
reactive() => 內部通常會是物件型態


defineProps  取得從父傳過來的參數

-->

<script setup>
  import {ref} from "vue";
  const oneWayData = "--------單向綁定的方式 {{ 定義在script內的變數 }}"
  const twoWayData = ref("需要透過ref()來進行動態的變換")


  defineProps({
    msg: String,
  })

</script>

<template>
  <h1>{{msg}}</h1>

  <div class = "container-1">
    <h2>資料綁定(單向)</h2>
    <p>{{oneWayData}}</p>
  </div>
  <br>

  <div class = "container-2">
  <h3>資料綁定(雙向)</h3>
  <input type="text" v-model="twoWayData" />
  <p>{{twoWayData}}</p>
  </div>

</template>

<style>
.container-1{
  border: 3px  brown solid;
  background: gainsboro;
}
.container-2{
  border: 2px  rebeccapurple dashed;
  background: gainsboro;
}

</style>



