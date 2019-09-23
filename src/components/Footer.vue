<template>
  <div class="footer">
    <el-row :gutter="24">
      <el-col :span="6">
        <div>
          <span>网站介绍</span>
        </div>
      </el-col>
      <el-col :span="6">
        <div>
          <span>登录方式</span>
        </div>
      </el-col>
      <el-col :span="6">
        <div>
          <span>意见反馈、使用许可</span>
        </div>
      </el-col>
      <el-col :span="6">
        <div>
          <span>返回顶部</span>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  props: {},
  methods: {},
  data() {
    return {};
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.l-col {
  border-radius: 4px;
}
.bg-purple-dark {
  background: #99a9bf;
}
.bg-purple {
  background: #d3dce6;
}
.bg-purple-light {
  background: #e5e9f2;
}
.grid-content {
  border-radius: 4px;
  min-height: 36px;
}
.row-bg {
  padding: 10px 0;
  background-color: #f9fafc;
}
</style>
