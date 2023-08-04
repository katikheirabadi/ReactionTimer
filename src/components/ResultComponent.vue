<template>
    <Transition>
        <div class="result">
           <h1>{{ rank }}</h1>
           <p>Reaction Time : {{ time }}</p>
        </div>
    </Transition>
</template>
<script>
export default {
    props: ['time'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
       if(this.time<250){
        this.rank = 'Wow! You are so fast'
       }else if(this.time < 500){
        this.rank = 'You are fast'
       }else if(this.time < 800){
        this.rank = 'It is Normal'
       }else{
        this.rank = 'You are slowly'
       }
    }
}
</script>
<style>
.result {
    width: 300px;
    border-radius: 30px;
    background-color: rgba(8, 83, 93, 0.525);
    color: white;
    text-align: center;
    padding: 50px 0;
    margin: 40px auto;
    font-size: 15px;
}

.v-enter-active,.v-leave-active{
    transition: opacity 0.5s ease;
}
.v-enter-from,.v-leave-to{
    opacity: 0;
}
</style>