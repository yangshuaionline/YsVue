<template>
  <div>
    <!-- 选择图片后展示 -->
    <img :src="f.src" width="100px" height="100px" v-if="f" />
    <!-- 选择图片之前展示 -->
    <img src="../assets/logo.png" @click="add()" width="100px" height="100px" v-else />
    <input
      class="value"
      style="display:none"
      type="file"
      ref="file"
      accept="image/*"
      multiple="multiple"
      @change="getFile($event)"
    />
    <span @click="submitForm($event)">上传</span>
    <img :src="loadImage" width="100px" height="100px" />
  </div>
</template>

<script>
import axios from "axios";
export default {
  props: {},
  data() {
    return {
      file: null,
      f: null,
      loadImage: ""
    };
  },
  methods: {
    add() {
      this.$refs.file.click();
    },
    getFile(event) {
      this.file = event.target.files[0];
      const item = {
        name: this.file.name,
        size: this.file.size,
        file: this.file
      };
      this.html5Reader(this.file, item);
      this.f = item;
    },
    // 将图片文件转成BASE64格式
    html5Reader(file, item) {
      const reader = new FileReader();
      reader.onload = e => {
        this.$set(item, "src", e.target.result);
      };
      reader.readAsDataURL(file);
    },
    submitForm(event) {
      event.preventDefault();
      let formData = new FormData();
      formData.append("file", this.file);
      let config = {
        headers: {
          "Content-Type": "multipart/form-data"
        }
      };
      axios
        .post("http://localhost:8888/test/upload", formData, config)
        .then(res => {
          console.log(res);
          if (res.status === 200) {
            try {
              console.log("http://localhost:8888/test/getImage/" + res.data);
              if (typeof this.loadImage !== "undefined") {
                this.loadImage =
                  "http://localhost:8888/test/getImage/" + res.data;
                console.log("aaa" + this.loadImage);
              }
              console.log("aaa" + 300);
            } catch (e) {
              console.log("捕获到异常：", e);
            }
          } else {
            console.log("aaa" + 400);
          }
        });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
