<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click me
    </div>
</template>

<script>
export default {
    props: [
        'delay'
    ],

    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },

    mounted() {
        console.log('Block MOUNTED')

        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },

    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },

        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)

            console.log('Reaction: ', this.reactionTime)
        }
    }
}
</script>

<style>
.block {
    padding: 100px 0;
    margin: 40px auto;

    width: 400px;

    color: white;
    text-align: center;

    background: #0faf87;
    border-radius: 20px;
}
</style>
