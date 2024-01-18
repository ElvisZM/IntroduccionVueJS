<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
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
      this.delayPadre = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.isPlaying = false
      this.showResults = true
      this.score = reactionTime
      document.getElementById('play_btn').innerText = 'Play Again'
    }
  }
}

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

  </header>

  <main>
    <h1>Ninja Reaction Timer</h1>
    <div>
      <button @click="start" id="play_btn" :disabled="isPlaying">Play</button>
    </div>
    <Block v-if="isPlaying" :delay="delayPadre" @end="endGame"/>
    <Results v-if="showResults" :score="score"/>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

h1 {
  border-bottom: 1px solid #ccc;
  width: 100%;
  text-align: center;
  margin-bottom: 20px;
}

button {
  margin: auto 45%;
  padding: 10px 20px;
  border-radius: 5px;
  border: 1px solid #ccc;
}

</style>
