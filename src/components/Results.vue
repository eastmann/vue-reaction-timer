<template>
    <p class="results">Reaction time: {{ score }} ms.</p>
    <p class="rank">Rank: {{ rank }}</p>
</template>

<script>
export default {
    props: [
        'score'
    ],

    data() {
        return {
            rank: null
        }
    },

    mounted() {
        if (this.score < 250 ) {
            this.rank = 'Ninja Fingers'
        } else if (this.score < 400) {
            this.rank = 'Rapid Reflexes'
        } else {
            this.rank = 'Snail Pace'
        }
    }
}
</script>

<style>
.results {
    padding: 100px 0;
    margin: 40px auto;

    width: 400px;

    color: white;
    text-align: center;

    background: crimson;
    border-radius: 20px;
}

.rank {
    color: #0faf87;
    font-size: 1.4em;
    font-weight: bold;
}
</style>
