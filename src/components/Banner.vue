<template>
  <div class="banner">
    <img src="public/image/logo.png" width="50px" height="50px" />
    <div class="a">
      <h2>Hello World</h2>
    </div>
    <div class="seach">
      <input type="text" class="input1" placeholder="Từ khóa" />
      <input type="button" value="Tìm kiếm" class="input2" />
    </div>
  </div>
</template>

<script>
export default {
  name: "BannerVue",
  data() {},
  props: {},
};
</script>

<style scoped>
.banner {
  width: 100%;
  height: 80px;
  background-color: aqua;
  display: flex;
}
.banner img {
  padding: 15px 30px 15px 30px;
}
.banner .a {
  width: 70%;
  text-align: center;
}
.banner .a h2 {
  color: rgba(255, 6, 6, 0.793);
}

.banner .seach {
  width: 400px;
}
.banner .seach .input1 {
  border-radius: 20px;
  width: 200px;
  height: 39px;
  color: #000000;
  border: none;
  position: relative;
  padding-left: 20px;
  padding-right: 50px;
  outline: none;
  margin-top: 20px;
}
.banner .seach .input2 {
  border-radius: 20px;
  width: 100px;
  height: 40px;
  background-color: #21243d;
  color: white;
  font-weight: bold;
  position: absolute;
  margin-left: -40px;
  border: none;
  margin-top: 20px;
}
</style>
