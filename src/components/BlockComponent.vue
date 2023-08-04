<template>
    <Transition>
        <div class="block" v-if="isshow" @click="stopTimer">
            Click Me Faster...
        </div>
    </Transition>
</template>
<script>
export default {
    props: ['delay'],
    data() {
        return {
            isshow: false,
            timer: null,
            reactionTime : 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.isshow = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10);
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end',this.reactionTime)
        }
    }
}
</script>
<style>
.block {
    width: 300px;
    border-radius: 30px;
    background-color: rgb(16, 16, 66);
    color: white;
    text-align: center;
    padding: 50px 0;
    margin: 40px auto;
    font-size: 35px;
}

.v-enter-active,.v-leave-active{
    transition: opacity 0.5s ease;
}
.v-enter-from,.v-leave-to{
    opacity: 0;
}
</style>