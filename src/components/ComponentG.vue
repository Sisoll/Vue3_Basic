<!--
slot  將component中挖洞，讓父


-->

<script setup>

import  ComponentG_child from './ComponentG_child.vue'
import {Icon } from '@vicons/utils'
import { Document } from '@vicons/carbon'

defineProps({
    msg: String,
    }
)

</script>


<template>
  <h1>{{msg}}</h1>

  <div>
    <ComponentG_child>
      <!--      沒有用名字就是default，會套用到所有沒有name的 slot內
                原本props傳的字串可以變成其他內容-->
      <Icon><Document/></Icon>

      <!--      針對特定的slot 傳值-->
      <template #getValue = "{val}">
        {{val}}
      </template>

      <!--      針對特定的slot-->
      <template #btns>
        <button>編輯</button>
        <button>設定</button>
      </template>


    </ComponentG_child>

  </div>


</template>



<style>
</style>



