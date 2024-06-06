<!--<script setup>-->
<!--import HelloWorld from './components/HelloWorld.vue'-->
<!--</script>-->

<template>
<!--  //左上角-->
  <el-radio-group v-model="isCollapse" class="left_bt" style="margin-bottom: auto">
    <el-radio-button  :value="false">展开</el-radio-button>
    <el-radio-button :value="true">折叠</el-radio-button>
  </el-radio-group>
<!--  //左侧菜单-->
<el-menu
  default-active="2"
  class="left_menu"
  id="left_menu"
  :collapse="isCollapse"
  @open="handleOpen"
  @close="handleClose"
>
  <el-sub-menu index="1">
    <template #title>
      <el-icon><location /> </el-icon>
      <span>设备管理</span>
    </template>

      <el-menu-item index="1-1" @click="handleMenuItemClick('1-1')">设备台账管理</el-menu-item>
      <el-menu-item index="1-2" @click="handleMenuItemClick('1-2')">设备状态监测</el-menu-item>
      <el-menu-item index="1-3" @click="handleMenuItemClick('1-3')">关键参数的展示与报警</el-menu-item>

  </el-sub-menu>

  <el-menu-item index="2">
    <el-icon><Histogram /></el-icon>
    <template #title>库存管理</template>
  </el-menu-item>

    <el-menu-item index="3">
    <el-icon><Coordinate /></el-icon>
    <template #title>质量管理</template>
  </el-menu-item>

    <el-menu-item index="4">
    <el-icon><Wallet /></el-icon>
    <template #title>成本管理</template>
  </el-menu-item>

  <el-menu-item index="5">
    <el-icon><UserFilled /></el-icon>
    <template #title>人力资源管理</template>
  </el-menu-item>

  <el-menu-item index="6">
    <el-icon><DArrowRight /></el-icon>
    <template #title>工序管理</template>
  </el-menu-item>

  <el-menu-item index="7">
    <el-icon><Notebook /></el-icon>
    <template #title>文档管理</template>
  </el-menu-item>

</el-menu>
  <!--  //台账信息-->
  <el-table :data="tableData"  v-show="showTable" height="auto" style="width: auto">
    <el-table-column prop="id" label="id" width="180" />
    <el-table-column prop="Equipment_number" label="Equipment_number" width="180" />
    <el-table-column prop="user_Factory" label="user_Factory" width="180" />
    <el-table-column prop="Equipment_type" label="Equipment_type" width="180" />
    <el-table-column prop="Device_name" label="Device_name" width="180" />
    <el-table-column prop="Matters_needing_attention" label="Matters_needing_attention" width="180" />
  </el-table>

  <!--  //状态信息    开关机-->
  <el-table :data="tableData_status"  v-show="showTable_status" height="auto" style="width: auto">
    <el-table-column prop="设备id" label="设备id" width="180" />
    <el-table-column prop="是否开机" label="是否开机" width="180" />
    <el-table-column prop="是否正常运行" label="是否正常运行" width="180" />
  </el-table>

    <!--  //报警信息-->
  <el-table :data="tableData_alarm"  v-show="showTable_alarm" height="auto" style="width: auto">
    <el-table-column prop="点表序号" label="点表序号" width="180" />
    <el-table-column prop="报警时间" label="报警时间" width="180" />
    <el-table-column prop="名称" label="名称" width="180" />
    <el-table-column prop="数据类型" label="数据类型" width="180" />
    <el-table-column prop="地址" label="地址" width="180" />
    <el-table-column prop="注释" label="注释" width="180" />
  </el-table>


</template>

<script lang="js" setup>
import { ref } from 'vue'

import {    //引入图标
  Menu as IconMenu,
  Location,
  Setting,
} from '@element-plus/icons-vue'

const isCollapse = ref(false)  //左侧菜单是否折叠
const showTable = ref(false)
const showTable_status = ref(false)
//报警信息
const showTable_alarm = ref(false)


const handleOpen = (key, keyPath) => { //菜单打开
  console.log(key, keyPath)
}

const handleClose = (key , keyPath) => {
  console.log(key, keyPath)
}

const handleMenuItemClick = (index) => {
  if (index === '1-1') {
    showTable.value = true
  } else {
    showTable.value = false
  }
    if (index === '1-2') {
    showTable_status.value = true
  } else {
    showTable_status.value = false
  }

  if (index === '1-3') {
    showTable_alarm.value = true
  } else {
    showTable_alarm.value = false
  }
}



const tableData_status = [
  {
    设备id: '设备id',
    是否开机: '是否开机',
    是否正常运行: '是否正常运行',
  }
]
const tableData_alarm = [
  {
    点表序号: '点表序号',
    报警时间: '报警时间',
    名称: '名称',
    数据类型: '数据类型',
    地址: '地址',
    注释: '注释',
  }
]
const tableData = [
  {
    id: '1',
    Equipment_number: 'Equipment_number',
    user_Factory: 'user_Factory',
    Equipment_type: 'Equipment_type',
    Device_name: 'Device_name',
    Matters_needing_attention: 'Matters_needing_attention',
  }
]



</script>

<style>
.left_bt{
  position: absolute; /* 绝对定位 */
  top: 0; /* 距离顶部为0 */
  left: 0; /* 距离左侧为0 */
  z-index: 999; /* 可能需要调整的层级 */
  /* 其他样式 */
}
#left_menu{
  position: absolute; /* 绝对定位 */
  top: 40px; /* 距离顶部为0 */
  left: 0; /* 距离左侧为0 */
  z-index: 999; /* 可能需要调整的层级 */
  /* 其他样式 */
}
</style>
