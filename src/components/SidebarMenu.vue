<template>
  <div class="sidebar">
    <el-menu
      class="sidebar-el-menu"
      text-color="#bfcbd9"
      background-color="#324157"
    >
      <template v-for="item in items">
        <template v-if="item.subs">
          <el-sub-menu :index="item.index" :key="item.index">
            <template #title>
              <el-icon>
                <component :is="item.icon"></component>
              </el-icon>
              <span>{{ item.title }}</span>
            </template>
            <template v-for="subItem in item.subs">
              <el-sub-menu
                v-if="subItem.subs"
                :index="subItem.index"
                :key="subItem.index"
              >
                <template #title>{{ subItem.title }}</template>
                <el-menu-item
                  v-for="(threeItem, i) in subItem.subs"
                  :key="i"
                  :index="threeItem.index"
                >
                  {{ threeItem.title }}
                </el-menu-item>
              </el-sub-menu>
              <el-menu-item>
                {{ subItem.title }}
              </el-menu-item>
            </template>
          </el-sub-menu>
        </template>
        <template v-else>
          <el-menu-item :index="item.index" :key="item.index">
            <el-icon>
              <component :is="item.icon"></component>
            </el-icon>
            <template #title>{{ item.title }}</template>
          </el-menu-item>
        </template>
      </template>
    </el-menu>
  </div>
</template>

<script lang="ts" setup>
const items = [
  {
    icon: 'Odometer',
    index: '/home',
    title: '系统首页',
  },
  {
    icon: 'Calender',
    index: '1',
    title: '表格相关',
    subs: [
      {
        index: '/table',
        title: '常用表格',
      },
      {
        index: '/import',
        title: '导入表格',
      },
      {
        index: '/export',
        title: '导出EXCEL',
      },
    ],
  },
  {
    icon: 'DocumentCopy',
    index: '/tabs',
    title: 'tab选项卡',
  },
  {
    icon: 'Edit',
    index: '3',
    title: '表单相关',
    subs: [
      {
        index: '/form',
        title: '基本表单',
      },
      {
        index: '/upload',
        title: '文件上传',
      },
      {
        index: '4',
        title: '基本表单',
        subs: [
          {
            index: '/editor',
            title: '富文本编辑器',
          },
          {
            index: '/markdown',
            title: 'markdown编辑器',
          },
        ],
      },
    ],
  },
  {
    icon: 'Setting',
    index: '/icon',
    title: '自定义图标',
  },
  {
    icon: 'PieChart',
    index: '/charts',
    title: '图表相关',
  },
  {
    icon: 'CoffeeCup',
    index: '/donate',
    title: '请我喝咖啡',
  },
]
</script>

<style scoped>
.sidebar {
  display: block;
  position: absolute;
  left: 0;
  top: 70px;
  bottom: 0;
  overflow-y: scroll;
}
.sidebar::-webkit-scrollbar {
  width: 0;
}
.sidebar-el-menu:not(.el-menu--collapse) {
  width: 250px;
}
.sidebar > ul {
  height: 100%;
}
</style>
