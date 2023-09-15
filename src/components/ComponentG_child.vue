<!--

-->

<script setup>
import {Icon } from '@vicons/utils'
import { Document ,Warning } from '@vicons/carbon'


</script>

<template>
  <div>
    <section>
      <Icon><Warning/></Icon>
      <!--等同
       <input v-show="title" placeholder="請輸入標題:"/>-->
      <slot/>

      <!-- slot 命名-->
      <slot name="btns"></slot>

      <!--直接傳值到父層-->
      <slot name="getValue" val="看到的這個值是從component直接傳出來的"></slot>


    </section>

  </div>


</template>



<style>
</style>



