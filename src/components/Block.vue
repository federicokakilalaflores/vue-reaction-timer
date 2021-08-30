<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click me
    </div>
</template>

<script>
    export default {
        name: 'Block',
        props: {
            delay: Number
        },
        data(){
            return{
                showBlock: false,
                timer: null,
                reactionTime: 0
            }
        },
        mounted(){
            setTimeout(()=>{
                this.showBlock = true
                this.startTimer()
            }, this.delay)
        },
        methods: {
             startTimer(){
                 this.timer = setInterval(() => {
                     this.reactionTime += 10
                 }, 10)
             },
             stopTimer(){
                 clearInterval(this.timer)
                 this.$emit('end', this.reactionTime);
             }
        }
    }
</script>

<style scoped>
    .block{
        justify-content: center;
        height: 250px;
        width: 450px;
        background-color: rgb(28, 189, 189);
        color: white; 
        display: flex;
        align-items: center;
        border-radius: 40px;
        margin: 2rem auto;
    }

    .block:hover{ cursor: pointer; }
</style>