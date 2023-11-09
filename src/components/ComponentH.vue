<!--
v-model 延伸=> 針對表單的綁定，其會忽略原有的value、checked、selected等屬性。
  修飾子
  v-model.lazy  (移開該處才會動作更新)
  v-model.number  (不然js會把數字當成字串)
  v-model.trim  (過濾頭尾)


ref() => 如果是物件型態需要 .value 才能取出值，如果是基本型態可以直接用。
reactive() => 內部通常會是物件型態


defineProps  取得從父傳過來的參數

-->

<script setup>
  import {ref} from "vue";
  const oneWayData = "--------單向綁定的方式 {{ 定義在script內的變數 }}"
  const twoWayData = ref("需要透過ref()來進行動態的變換")

  // radio
  const radioModel = ref('switch2')

  // checkbox
  const checkModel = ref([])

  // selected
  const selected = ref('')

  defineProps({
    msg: String,
  })

</script>

<template>
  <h1>{{msg}}</h1>

  <!--  單向綁定-->
  <div class = "container-1">
    <h2>資料綁定(單向)</h2>
    <p>{{oneWayData}}</p>
  </div>
  <br>

  <!--  雙向綁定-->
  <div class = "container-2">
  <h3>資料綁定(雙向) - text input</h3>
  <input type="text" v-model="twoWayData" />
  <p>{{twoWayData}}</p>
  </div>

  <div class="container-3">
    <h3>資料綁定(雙向) - text radio</h3>
    <input type="radio" id="switch1" value="switch1" v-model="radioModel">
    <label for="switch1">開關1</label>
    <input type="radio" id="switch2" value="switch2" v-model="radioModel">
    <label for="switch2">開關2</label>
    <input type="radio" id="switch3" value="switch3" v-model="radioModel">
    <label for="switch3">開關3</label>

    <p>the radio state at : {{radioModel}}</p>
  </div>

  <div class="container-3">
    <h3>資料綁定(雙向) - radio</h3>
    <input type="checkbox" id="check1" value="check1" v-model="checkModel">
    <label for="check1">開關1</label>
    <input type="checkbox" id="check2" value="check2" v-model="checkModel">
    <label for="check2">開關2</label>
    <input type="checkbox" id="check3" value="check3" v-model="checkModel">
    <label for="check3">開關3</label>

    <p>select with :  {{checkModel}}</p>
  </div>

  <div class="container-3">
  <!-- 注意v-model是要加在select-->
    <h3>資料綁定(雙向) - select</h3>
    <select v-model="selected">
      <option disabled value="">請選擇</option>
      <option>台北</option>
      <option>桃園</option>
      <option>高雄</option>
    </select>
    <p>select with :  {{selected || '未選'}}</p>
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

.container-3{
  border: 2px  rebeccapurple dashed;
}

</style>



