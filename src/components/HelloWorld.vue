<template>
  <div class="hello">
    <!-- <h1>{{ msg }}</h1> -->
    <h2>Tên: {{ array.name }}</h2>
    <h2>Giá: {{ format_Price() }}</h2>
    <button v-on:click="addCat()">Thêm vào giỏ</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    // msg: String,
    array: Object,
    monny: Number,
  },
  methods: {
    format_Price() {
      var number = this.array.price1;
      return new Intl.NumberFormat("de-DE", {
        style: "currency",
        currency: "VND",
      }).format(number);
    },
    addCat() {
      var data = this.array.price1;
      this.$emit("handleMonny", data);
    },
  },
};
</script>

<style scoped>
.hello {
  width: 20%;
  height: 20%;
  background-color: rgb(0, 174, 255);
  margin: 10px;
}
.hello button {
  width: 100px;
  margin: 10px;
  border-radius: 10px;
}
.hello button :hover {
  background-color: brown;
}
</style>
