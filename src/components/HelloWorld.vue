<template>
  <div class="hello">
    <el-container>
      <el-main>
        <div>
          <ul class="infinite-list" v-infinite-scroll="load()" style="list-style-type:none">
            <li v-for="i in count" :key="i" class="infinite-list-item">
              <div>
                <img class="img" src="../assets/logo.png" />
                <h1 class="h1">介绍{{i}}</h1>
              </div>
            </li>
          </ul>
        </div>
        <div class="hello_page">
          <el-pagination
            @size-change="handleSizeChange()"
            @current-change="handleCurrentChange()"
            :current-page.sync="currentPage"
            :page-size="100"
            layout="prev, pager, next, jumper"
            :total="1000"
          ></el-pagination>
        </div>
      </el-main>
      <el-footer>
        <Footer></Footer>
      </el-footer>
    </el-container>
  </div>
</template>

<script>
import Footer from "@/components/Footer.vue";

export default {
  name: "HelloWorld",
  components: {
    Footer
  },
  props: {
    msg: String
  },
  methods: {
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`);
    },
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
    },
    load() {
      this.count = 20;
    }
  },
  data() {
    return {
      currentPage: 1,
      count: 20
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.adv {
  width: 1000px;
  height: 200px;
  background-color: red;
}
.list {
  background-color: blue;
}
.line {
  width: 1px;
  height: 1000px;
  background-color: black;
}
.aaa {
  /*main上面空白一部分，不然会遮挡布局*/
  height: 80px;
}
.el-header,
.el-footer {
  background-color: #e9eef3;
  color: #333;
  text-align: center;
  line-height: 60px;
}

.el-aside {
  background-color: #d3dce6;
  color: #333;
  text-align: center;
  /* line-height: 200px; */
}

.el-main {
  background-color: #e9eef3;
  color: #333;
  text-align: center;
  line-height: 160px;
}
.hello_page {
  width: 100%;
  /* height: 40px; */
  /* background-color: red; */
  float: left;
}
.img {
  width: 10%;
  height: 150px;
  float: left;
}
.h1 {
  width: 90%;
  height: 150px;
  float: left;
}
</style>
