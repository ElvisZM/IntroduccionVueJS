<template>
    <div class="block" v-if="showBlock">
        Click Me
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        console.log('component mounted')
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            console.log(this.delay)
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
        }

    }
}
</script>

<style>
    .block {
        width: 400px;
        background-color: aquamarine;
        color: white;
    }


</style>


