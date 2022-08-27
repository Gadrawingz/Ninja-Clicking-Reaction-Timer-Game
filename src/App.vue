<template>
  <div class="box">
    <h1> {{ gameTitle }}</h1>
    <h2> {{ gameSubTitle }} </h2>
    <button @click="start" :disabled="isPlaying">Start Playing</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <!-- <p v-if="showResults">Reaction time is {{ score }} ms.</p> -->
    <Resultance v-if="showResults" :score="score" />
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Resultance from "./components/Resultance.vue";

export default {
  name: "App",
  components: {
    Block, Resultance,
  },

  data() {
    return {
      gameTitle: "Clickin' Super Ninja",
      gameSubTitle: "Reaction Timer Game...",
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },

  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.box {
  /* border-left: 10px solid blue; */
  border: 1px solid #000;
  border-radius: 5px;
  background: #d5f5e3;
}

.box h1{
  font-family: Georgia, 'Times New Roman', Times, serif;
  border-bottom: 10px solid blue;
  color: blue;
  font-size: 28px;
  padding: 10px;
}

.box h2 {
  font-family: Consolas;
  font-size: 18px;
  padding: 10px;
  text-decoration: underline;
}

button {
  background: #1b4f72;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
