<template>
  <el-menu
    :default-active="activeIndex"
    class="el-menu-demo"
    mode="horizontal"
    router
    @select="handleSelect"
  >
    <template v-for="item in routes">
      <el-submenu :index="item.path" :key="item.path" v-if="item.children">
        <template #title>{{ item.name }}</template>
        <el-menu-item
          :index="itm.path"
          v-for="itm in item.children"
          :key="itm.path"
          >{{ itm.name }}</el-menu-item
        >
      </el-submenu>
      <el-menu-item :index="item.path" :key="item.path" v-else>
        {{ item.name }}
      </el-menu-item>
    </template>
  </el-menu>
</template>

<script lang='ts'>
import { Vue } from "vue-class-component";
export default class Menu extends Vue {
  private activeIndex = "/index";
  private routes = [
    {
      path: "/index",
      name: "首页",
    },
  ];
  private handleSelect(key, keyPath) {
    console.log(key, keyPath);
  }
}
</script>

<style>
</style>