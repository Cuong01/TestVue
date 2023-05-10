<template>
  <div id="app">
    <Banner />
    <div class="demo">
      <button v-on:click="type = 0">Mảng</button>
      <button v-on:click="type = 1">Test</button>
      <button v-on:click="type = 2">Game</button>
    </div>
    <div v-if="type == 0">
      <Menu />
    </div>
    <div v-if="type == 1">
      <div class="sum">
        <h1>Tổng tiền: {{ format_Price() }}</h1>
      </div>
      <div class="a">
        <HelloWorld
          v-for="(item, k) in list"
          :key="k"
          :array="item"
          :monny="monny"
          v-on:handleMonny="handleMonny"
        />
      </div>
    </div>
    <div v-if="type == 2">
      <Game />
    </div>
  </div>
</template>

<script>
import Menu from "./components/Menu.vue";
import HelloWorld from "./components/HelloWorld.vue";
import Game from "./components/Game.vue";
import Banner from "./components/Banner.vue";

export default {
  name: "App",
  data() {
    return {
      list: [
        { name: "A", price1: 10000 },
        { name: "B", price1: 20000 },
        { name: "C", price1: 30000 },
        { name: "D", price1: 40000 },
        { name: "E", price1: 50000 },
        { name: "F", price1: 60000 },
        // { name: "G", price1: 70000 },
      ],
      monny: 0,
      type: 0,
    };
  },
  methods: {
    format_Price() {
      var number = this.monny;
      return new Intl.NumberFormat("de-DE", {
        style: "currency",
        currency: "VND",
      }).format(number);
    },
    handleMonny(data) {
      return (this.monny += data);
    },
  },

  components: {
    Menu,
    HelloWorld,
    Banner,
    Game,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.a {
  text-align: center;
  display: flex;
}

.demo {
  text-align: center;
  background-color: #ccc;
}

.demo button {
  cursor: pointer;
  padding: 10px 20px;
  background-color: rgb(175, 254, 130);
  border-radius: 4px;
  margin: 0 10px;
}
</style>
