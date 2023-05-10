<template>
  <div>
    <div class="test">
      <div class="createNumber">
        <div class="a1">
          <label>Các đối tượng có type = 1: </label>
          <b v-for="(item, k) in checkType" :key="k">{{ item.value }}</b>
        </div>
        <input type="number" v-model="n" />
        <button v-on:click="addNumber()">Thêm vào mảng</button>
        <div style="display: flex">
          <p v-for="(item1, k) in array2" :key="k" v-on:click="deleteArray(k)">
            {{ item1 }}
          </p>
        </div>
        <button v-on:click="Tangdan()">Sắp xếp mảng tăng dần</button>
        <button v-on:click="Giamdan()">Sắp xếp mảng tăng dần</button>
      </div>

      <div style="display: flex">
        <div class="updateNumber">
          <p>
            <label for="">Vị trí cần thay đổi: </label>
            <input type="number" v-model="numberOld" />
          </p>
          <h3 v-if="check == false">Trong mảng không chứa:</h3>
          <p>
            <label for="">Đổi thành: </label>
            <input type="number" v-model="numberNew" />
          </p>
          <button v-on:click="updateArray()">Thay thế</button>
        </div>
        <div class="seachNumber">
          <label>Vị trí phần tử: </label>
          <input type="number" v-model="a" />
          <div v-for="(item2, k) in array2" :key="k">
            <p v-if="k == a">Phần tử: {{ item2 }}</p>
          </div>
        </div>
        <div class="seach">
          <label>Số cần tìm: </label>
          <input type="number" v-model="keySeach" />
          <button v-on:click="seachArray()">Tìm kiếm</button>
          <h3 v-if="active == true">Trong mảng có chứa</h3>
          <h3 v-if="active == false">Trong mảng không chứa</h3>
        </div>
      </div>

      <div class="price">
        <h1>{{ format_Price() }}</h1>
        <div>
          <button v-on:click="cong()">+200.000</button>
          <button v-on:click="tru()">-200.000</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MenuVue",
  // props: array2,
  data() {
    return {
      arrays: [
        { value: "a", type: 1 },
        { value: "b", type: 0 },
        { value: "c", type: 0 },
        { value: "d", type: 1 },
      ],
      array2: [1, 31, 12, 4, 5, 6, 3, 2],
      n: 0,
      a: 0,
      b: 0,
      keySeach: "",
      active: false,
      numberOld: "",
      numberNew: "",
      check: true,
      price: 1000000,
    };
  },
  props: {},
  methods: {
    addNumber() {
      this.array2.push(Number(this.n));
    },
    Tangdan() {
      return this.array2.sort((a, b) => a - b);
    },
    Giamdan() {
      return this.array2.sort((a, b) => b - a);
    },
    deleteArray(key) {
      alert("Xóa thành công");
      return this.array2.splice(key, 1);
    },
    seachArray() {
      return (this.active = this.array2.includes(Number(this.keySeach)));
    },
    updateArray() {
      this.array2[this.numberOld] = Number(this.numberNew);
      console.log(this.array2);
    },
    format_Price() {
      var number = this.price;
      return new Intl.NumberFormat("de-DE", {
        style: "currency",
        currency: "VND",
      }).format(number);
    },
    cong() {
      return (this.price += 200000);
    },
    tru() {
      return (this.price -= 200000);
    },
  },
  computed: {
    checkType() {
      return this.arrays.filter(function (a) {
        return a.type == 1;
      });
    },
  },
  components: {},
};
</script>

<style scoped>
.test {
  background-color: azure;
}
.createNumber {
  padding: 40px;
}

.createNumber .a1 {
  padding: 20px 0;
}

.createNumber .a1 b {
  padding: 10px;
}

.createNumber p {
  background-color: rgb(248, 251, 173);
  padding: 20px;
  font-size: 20px;
  width: auto;
  display: flex;
  border: 1px solid rgb(203, 203, 203);
}
.updateNumber {
  padding: 30px;
  width: 33%;
  background-color: rgb(4, 247, 251);
}
.seachNumber {
  padding: 30px;
  width: 33%;
  background-color: rgb(233, 252, 62);
}
.seach {
  padding: 30px;
  width: 34%;
  background-color: rgb(254, 249, 119);
}
.price {
  width: 33%;
  height: 200px;
  background-color: rgb(235, 163, 255);
  text-align: center;
}
.price h1 {
  padding-top: 40px;
}
input {
  width: 200px;
  height: 40px;
  border-radius: 5px;
  padding: 5px 10px;
  margin: 5px;
}
button {
  /* width: 100px; */
  cursor: pointer;
  height: 40px;
  background-color: rgb(255, 192, 3);
  border-radius: 10px;
  margin: 5px;
  padding: 5px 10px;
}
button:hover {
  /* width: 100px; */
  height: 40px;
  background-color: rgb(63, 228, 22);
  border-radius: 10px;
  margin: 5px;
  padding: 5px 10px;
}
</style>
