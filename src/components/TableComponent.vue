<template>
  <!--  //台账信息-->
  <el-table :data="tableData" v-show="showTable" height="auto" style="width: auto">
    <el-table-column prop="id" label="id" width="180" />
    <el-table-column prop="Equipment_number" label="Equipment_number" width="180" />
    <el-table-column prop="user_Factory" label="user_Factory" width="180" />
    <el-table-column prop="Equipment_type" label="Equipment_type" width="180" />
    <el-table-column prop="Device_name" label="Device_name" width="180" />
    <el-table-column prop="Matters_needing_attention" label="Matters_needing_attention" width="180" />
  </el-table>

  <!--  //状态信息    开关机-->
  <el-table :data="tableDataStatus" v-show="showTableStatus" height="auto" style="width: auto">
    <el-table-column prop="设备id" label="设备id" width="180" />
    <el-table-column prop="是否开机" label="是否开机" width="180" />
    <el-table-column prop="是否正常运行" label="是否正常运行" width="180" />
  </el-table>

  <!--  //报警信息-->
  <el-table :data="tableDataAlarm" v-show="showTableAlarm" height="auto" style="width: auto">
    <el-table-column prop="点表序号" label="点表序号" width="180" />
    <el-table-column prop="报警时间" label="报警时间" width="