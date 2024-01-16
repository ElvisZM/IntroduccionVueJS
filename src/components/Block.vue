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
        }
    },
    mounted() {
        console.log('component mounted')
        setTimeout(() => {
            this.showBlock = true
            console.log(this.delay)
        }, this.delay)
    },
    updated() {

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


