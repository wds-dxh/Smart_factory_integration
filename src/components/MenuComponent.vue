<template>
  <el-menu
    default-active="2"
    class="left_menu"
    :collapse="isCollapse"
    @open="handleOpen"
    @close="handleClose"
  >
    <el-sub-menu index="1">
      <template #title>
        <el-icon><location /> </el-icon>
        <span>设备管理</span>
      </template>
      <el-menu-item index="1-1" @click="handleMenuItemClick">设备台账管理</el-menu-item>
      <el-menu-item index="1-2" @click="handleMenuItemClick">设备状态监测</el-menu-item>
      <el-menu-item index="1-3" @click="handleMenuItemClick">关键参数的展示与报警</el-menu-item>
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
</template>

<script lang="js" setup>
import { ref, emit } from 'vue'

const props = defineProps({
  isCollapse: Boolean,
});

const handleOpen = (key, keyPath) => { // 菜单打开
  console.log(key, keyPath)
}

const handleClose = (key , keyPath) => {  // 菜单关闭
  console.log(key, keyPath)
}

const handleMenuItemClick = (index) => { // 菜单点击
  emit('menu-item-click', index)
}
</script>

<style>
#left_menu {
  position: absolute; /* 绝对定位 */
  top: 40px; /* 距离顶部为0 */
  left: 0; /* 距离左侧为0 */
  z-index: 999; /* 可能需要调整的层级 */
  /* 其他样式 */
}
</style>