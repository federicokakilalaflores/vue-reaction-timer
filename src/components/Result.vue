<template>
    <div class="score-wrapper">
       Your Reaction Time: <span class="score">{{ score }} ms</span>
    </div>
    <p class="rank">{{ rank }}</p> 
</template>

<script>
export default {
    name: 'Result',
    props: {
        score: Number
    },
    data(){
        return {
            rank: null 
        }
    },
    mounted(){
        if(this.score < 250){
            this.rank = "Great Job Reflex!";
        }else if(this.score < 600){
            this.rank = "Pretty Good Reflex!";
        }else{
            this.rank = "Poor Reflex!";
        }
    }
}
</script>

<style scoped>
.score-wrapper{
    margin-top: 1rem;
    font-size: 1.1rem;
}
 span.score{
     font-weight: 900;
 } 

 .rank{
     font-size: 1.2rem;
     font-weight: bold;
     font-style: italic;
 }
</style>