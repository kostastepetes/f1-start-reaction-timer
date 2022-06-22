<template>
  <h1>F1 Start Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
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
html, body {
  margin:0px;
  height:100%;
  background-image: url("https://media.istockphoto.com/vectors/race-flag-finish-flag-vector-isolated-illustration-race-flag-icon-vector-id1253533380?k=20&m=1253533380&s=612x612&w=0&h=MTtqfAPGfgKN6DbHU7CCNklrMZ6ZZHj52sMh_UpGNm4=");
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: rgb(173, 43, 43);
  height: 100%;
  width: 100%;
  margin-top: 15px;
  padding-top: 10px;
  background-image: url("https://wallpaperaccess.com/full/6122394.png");
  background-position: center; /* Center the image */
}
button {
  background: #273044;
  color: white;
  border: none;
  padding: 8px 16px;
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
