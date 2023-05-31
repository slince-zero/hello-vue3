<template>
  <div class="common-layout">
    <el-container>
      <el-aside>
        <SidebarMenu></SidebarMenu>
      </el-aside>
      <el-container>
        <el-header>Header</el-header>
        <el-main>Main</el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script setup lang="ts">
import SidebarMenu from '../components/SidebarMenu.vue'
</script>
