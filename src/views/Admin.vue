<template>
  <!-- 后台管理页面 -->
  <el-container style="border: 1px solid #eee">
    <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
      <!--默认展开  :default-active="getCurrent()"-->
      <el-menu :default-openeds="['1','2']">
        <el-submenu index="1">
          <template slot="title">
            <i class="el-icon-message"></i>数据库管理
          </template>
          <el-menu-item index="1-1" @click="onLeftClick(1)">文章库</el-menu-item>
          <el-menu-item index="1-2" @click="onLeftClick(2)">图片库</el-menu-item>
          <el-menu-item index="1-3" @click="onLeftClick(3)">点赞库</el-menu-item>
          <el-menu-item index="1-4" @click="onLeftClick(4)">评论库</el-menu-item>
          <el-menu-item index="1-5" @click="onLeftClick(5)">用户库</el-menu-item>
        </el-submenu>
        <el-submenu index="2">
          <template slot="title">
            <i class="el-icon-message"></i>功能
          </template>
          <el-menu-item index="2-1" @click="onLeftClick(6)">上传图片</el-menu-item>
        </el-submenu>
      </el-menu>
    </el-aside>

    <el-container>
      <el-header style="text-align: right; font-size: 12px">
        <el-dropdown>
          <i class="el-icon-setting" style="margin-right: 15px"></i>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item>查看</el-dropdown-item>
            <el-dropdown-item>新增</el-dropdown-item>
            <el-dropdown-item>删除</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
        <span>王小虎</span>
      </el-header>

      <el-main>
        <span v-if="current == 0">测试</span>
        <el-table :data="tableData" v-if="current == 1">
          <el-table-column prop="date" label="111日期" width="140"></el-table-column>
          <el-table-column prop="name" label="姓名" width="120"></el-table-column>
          <el-table-column prop="address" label="地址"></el-table-column>
        </el-table>
        <el-table :data="tableData" v-if="current == 2">
          <el-table-column prop="date" label="222日期" width="140"></el-table-column>
          <el-table-column prop="name" label="姓名" width="120"></el-table-column>
          <el-table-column prop="address" label="地址"></el-table-column>
        </el-table>
        <el-table :data="tableData" v-if="current == 3">
          <el-table-column prop="date" label="333日期" width="140"></el-table-column>
          <el-table-column prop="name" label="姓名" width="120"></el-table-column>
          <el-table-column prop="address" label="地址"></el-table-column>
        </el-table>
        <el-table :data="tableData" v-if="current == 4">
          <el-table-column prop="date" label="444日期" width="140"></el-table-column>
          <el-table-column prop="name" label="姓名" width="120"></el-table-column>
          <el-table-column prop="address" label="地址"></el-table-column>
        </el-table>
        <el-table :data="tableData" v-if="current == 5">
          <el-table-column prop="date" label="555日期" width="140"></el-table-column>
          <el-table-column prop="name" label="姓名" width="120"></el-table-column>
          <el-table-column prop="address" label="地址"></el-table-column>
        </el-table>
        <UpImg v-if="current == 6"></UpImg>
      </el-main>
    </el-container>
  </el-container>
</template>
<style>
.el-header {
  background-color: #b3c0d1;
  color: #333;
  line-height: 60px;
}

.el-aside {
  color: #333;
}
</style>

<script>
import UpImg from "@/components/UpImg.vue";
export default {
  components: {
    UpImg
  },
  data() {
    const item = {
      date: "2016-05-02",
      name: "王小虎",
      address: "上海市普陀区金沙江路 1518 弄"
    };
    return {
      tableData: Array(20).fill(item),
      current: 0
    };
  },
  methods: {
    onLeftClick: function(index) {
      this.current = index;
    }
  }
};
</script>
