<template>
  <div class="game">
    <div class="wrapper clearfix">
      <Player
        v-bind:scores="scores"
        v-bind:active="active"
        v-bind:current="current"
      />
      <Controls
        v-on:handleNewGame="handleNewGame"
        v-on:handleRollDice="handleRollDice"
        v-on:handleHold="handleHold"
      />
      <Dices v-bind:dices="dices" />
    </div>
  </div>
</template>

<script>
import Player from "./Game/Player.vue";
import Controls from "./Game/Controls.vue";
import Dices from "./Game/Dices.vue";

export default {
  name: "GameVue",
  data() {
    return {
      isPlaying: false,
      active: 1,
      scores: [1, 3],
      current: 10,
      dices: [1, 3],
    };
  },
  methods: {
    nextPlayer() {
      this.active = this.active == 0 ? 1 : 0;
      this.current = 0;
    },
    handleNewGame() {
      this.isPlaying = true;
      this.active = 0;
      this.current = 0;
      this.scores = [0, 0];
      this.dices = [1, 1];
    },
    handleRollDice() {
      if (this.isPlaying) {
        var x = Math.ceil(Math.random() * 6);
        var y = Math.ceil(Math.random() * 6);
        this.dices = [x, y];
        // console.log(x, y);
        if (x == 1 || y == 1) {
          setTimeout(function () {
            alert("Đổi người chơi");
          }, 100);
          this.nextPlayer();
        } else {
          this.current += x + y;
        }
      } else {
        alert("Vui lòng nhấn vào nút bắt đầu");
      }
    },
    handleHold() {
      // console.log("1");
      if (this.isPlaying) {
        this.scores[this.active] = this.scores[this.active] + this.current;
        if (this.scores[this.active] >= 100) {
          alert("Người chơi " + (this.active + 1) + " thắng cuộc");
          alert("Chơi tiếp");
          this.handleNewGame();
        }
        this.nextPlayer();
      } else {
        alert("Vui lòng nhấn vào nút bắt đầu");
      }
    },
    test() {
      if (this.isPlaying) {
        if (this.active == 1) {
          this.handleRollDice();
          if (this.current >= 10) {
            this.handleHold();
          }
        }
      }
    },
  },
  computed: {},
  components: {
    Player,
    Controls,
    Dices,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.clearfix::after {
  content: "";
  display: table;
  clear: both;
}
.game {
  background-image: linear-gradient(
      rgba(62, 20, 20, 0.4),
      rgba(62, 20, 20, 0.4)
    ),
    url("/public/image/back.jpg");
  background-size: cover;
  background-position: center;
  font-family: Lato;
  font-weight: 300;
  position: relative;
  height: 100vh;
  color: #555;
}

.wrapper {
  width: 1000px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #fff;
  box-shadow: 0px 10px 50px rgba(0, 0, 0, 0.3);
  overflow: hidden;
}
</style>
