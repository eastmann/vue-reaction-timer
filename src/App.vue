<template>
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
    <Results v-if="showResults" :score="score"></Results>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

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
            showResults: false
        }
    },

    methods: {
        start() {
            this.delay = this.random()
            this.isPlaying = true
            this.showResults = false
        },

        random() {
            return 2000 + Math.floor(Math.random() * 5000);
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
    color: #444;
    margin-top: 60px;
}

button {
    margin: 10px;
    padding: 8px 16px;

    color: white;
    font-size: 16px;
    letter-spacing: 1px;

    background: #0faf87;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button[disabled] {
    cursor: not-allowed;
    opacity: 0.2;
}
</style>
