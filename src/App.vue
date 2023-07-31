<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @block-clicked="endGame"></Block>
  <Results v-if="score != null" :score="score" :rank="rank"></Results>
</template>

<script>

import Block from './components/Block.vue';
import Results from './components/Results.vue';


export default {
  name: 'App',
  components: {
    Block,
    Results
  },

  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      rank: null,
    }
  },


  methods: {
    start() {
      this.score = null;
      this.rank = null;
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      console.log(this.delay);
    },

    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.setRank();

    },

    setRank() {

      if (this.score < 200) {
        this.rank = 'Godlike';

      } else if (this.score < 250) {
        this.rank = 'Pro';
      }
      else if (this.score < 300) {
        this.rank = 'Swift';
      } else if (this.score < 400) {
        this.rank = 'Average';

      } else if (this.score < 450) {
        this.rank = 'Slow';
      } else {
        this.rank = 'Turtle';
      }




    },


  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;


}

button {
  background-color: red;
  color: white;
  border: none;
  border-radius: 5px;
  width: 100px;
  height: 25px;
  font-weight: bold;
  cursor: pointer;
}

button[disabled] {
  background-color: grey;
  color: white;
  cursor: not-allowed;
}
</style>
