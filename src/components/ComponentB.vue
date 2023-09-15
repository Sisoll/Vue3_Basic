<!--
條件渲染顯示與點擊事件綁定{{}}
v-if、v-else、  => 直接將其node拿掉
v-show  => 透過 CSS 的disable呈現畫面與否


@click = v-on:click

-->

<script setup>
import {ref} from "vue";
const oneWayData = "--------單向綁定的方式 {{ 定義在script內的變數 }}"
const twoWayData = ref("需要透過ref()來進行動態的變換")

const view  = ref(0)
const changeView = (index) => {
  view.value = index
}

defineProps({
  msg: String,
})

</script>

<template>
  <h1>{{msg}}</h1>

  <button v-on:click="changeView(1)"> 顯示單向綁定</button>
  <button @click="changeView(2)" >顯示雙向綁定</button>
  <button @click="changeView(3)" >沒畫面</button>


  <div class = "container-1" v-if="view===1 " >
    <h2>資料綁定(單向)</h2>
    <p>{{oneWayData}}</p>
  </div>
  <br>

  <div class = "container-2" v-if="view===2">
    <h3>資料綁定(雙向)</h3>
    <input type="text" v-model="twoWayData" />
    <p>{{twoWayData}}</p>
  </div>

  <div v-if="view !==1 && view !==2">

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



