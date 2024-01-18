<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me!
    </div>
</template>

<script>
    export default {
        props: ['delay'],
        data() {
            return {
                showBlock: false,
                timer: null,
                reactionTime: 0
            }
        },
        mounted() {
            //console.log('mounted')
            setTimeout(() => {
                this.showBlock = true, this.startTimer()
            }, this.delay)
        },
        updated(){
            //console.log('updated')
        },
        unmounted() {
            //console.log('unmounted')
        },
        methods: {
            startTimer() {
                this.timer = setInterval(() => {
                    this.reactionTime += 10
                }, 10)
            },
            stopTimer() {
                clearInterval(this.timer)
                this.showBlock = false
                this.$emit('end', this.reactionTime)
            }
        }
    }

</script>

<style>
    .block {
        display: inline-block;
        width: 35%;
        background-color: aquamarine;
        color: white;
        margin: 15px 40%;
        border-radius: 10px;
        font-size: 1.5rem;
        
    }


</style>


