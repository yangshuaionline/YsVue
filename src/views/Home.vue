<template>
  <!-- 前端展示页面 -->
  <div class="home">
    <el-menu
      :default-active="activeIndex2"
      class="el-menu-demo"
      mode="horizontal"
      @select="handleSelect"
      background-color="#0593d3"
      text-color="#fff"
      active-text-color="#ffd04b"
    >
      <!-- <p class="home_logo" @click="firstClick()">学习使人进步</p> -->
      <el-menu-item index="1" class="home_logo">
        <span slot="title">学习使人进步</span>
      </el-menu-item>
      <el-menu-item index="2">
        <i class="el-icon-menu"></i>
        <span slot="title">Java</span>
      </el-menu-item>
      <el-menu-item index="3">
        <i class="el-icon-document"></i>
        <span slot="title">Vue</span>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <span slot="title">Android</span>
      </el-menu-item>
      <p class="home_white"></p>
      <el-menu-item index="5">
        <i class="el-icon-setting"></i>
        <span slot="title">登录</span>
      </el-menu-item>
      <el-submenu index="6">
        <template slot="title">多语言</template>
        <el-menu-item index="2-1">中文</el-menu-item>
        <el-menu-item index="2-2">English</el-menu-item>
      </el-submenu>
    </el-menu>
    <div class="header_top"></div>
    <div>
      <HelloWorld v-if="index == 1" />
      <p v-else-if="index == 2">Java</p>
      <p v-else-if="index == 3">Vue</p>
      <p v-else-if="index == 4">Android</p>
      <p v-else-if="index == 5">登录</p>
      <p v-else-if="index == 6">多语言</p>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "home",
  components: {
    HelloWorld
  },
  data() {
    return {
      activeIndex: "1",
      activeIndex2: "1",
      index: 1
    };
  },
  //自动触发
  mounted: function() {
    this.setWidth();
  },
  methods: {
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
      this.index = keyPath;
    },
    setWidth() {
      // let width = document.body.clientWidth;
      // var home_white = document.getElementsByClassName("home_white")[0];
      // home_white.style.widhth = width;
    }
  }
};
</script>

<style>
.home,/*设置占满*/
html,
body {
  width: 100%;
  height: 100%;
  margin: 0;
}
.el-menu-demo {
  width: 100%;
  position: fixed !important; /*悬浮*/
  top: 0px;
  right: 0px;
  z-index: 1;
  background-color: #0593d3;
}

/* .home_logo {
  width: 200px;
  color: white;
  /**多行文本设置居中*/
/* text-align: center;
  vertical-align: middle;
  display: table-cell;
  float: left;
  cursor: pointer;
} */
.home_white {
  width: 60%;
  float: left;
}
.header_top {
  /*main上面空白一部分，不然会遮挡布局*/
  height: 60px;
  background-color: #e9eef3;
}
</style>