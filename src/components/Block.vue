<template>
    <div v-if="boxShow" @click="endGame" class="block bg-success rounded shadow m-auto d-flex justify-center">
        <p v-if="!gamePause" class="text-white m-auto">click me :)</p>
        <p v-else class="text-white m-auto">GG :)</p>
    </div>
</template>

<script>

export default{
    props:['delay'],
    data(){
        return {
            boxShow:false,
            reactionTime:null,
            reactionTimeScore:null,
            gamePause:false,
        }
    },
    mounted(){
        setInterval(() => {
            this.boxShow = true
            this.reactionTimeCalc()
        },this.delay)
    },
    methods:{
        reactionTimeCalc(){
            this.reactionTime = setInterval(() => {
                this.reactionTimeScore += 10
            },10)
        },
        endGame(){
            if(this.gamePause == false){
                this.gamePause = true
                clearInterval(this.reactionTime)
                this.$emit('end',this.reactionTimeScore)
            }else{
                this.gamePause = true
            }
        }
    }
}
</script>

<style>
 .block{
    height: 200px;
    width: 350px;
    cursor: pointer;
 }
</style>