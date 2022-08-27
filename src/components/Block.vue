<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me
    </div>
</template>
<!-- Lets go n get it -->
<script>
export default {
    props : ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        console.log("Our component is mounted!")
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
            this.$emit('end', this.reactionTime)
            console.log(this.reactionTime)
        }
    }
}
</script>

<style>
.block {
    width: 420px;
    border-radius: 18px;
    background: blue;
    color: white;
    font-size: 40px;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>