<template>
    <div 
        v-if="showBlock" 
        class="block"
        @click="finish">
        <p>Click Me!!!</p>
    </div>
</template>

<script>
export default {
    name:"Block",
    props:["delay"],
    data(){
        return{
            showBlock:false,
            timer:null,
            reactionTime:0
        }
    },
    // watch:{
    //     showBlock(from,to){
    //         console.log(from)
    //         console.log(to)
    //     }
    // },
    // watch and updated have the same effect in our case
    mounted(){
        setTimeout(()=>{
            this.showBlock=true
            this.timer=setInterval(()=>{
                this.reactionTime += 10
            },10)
        }, this.delay)

    },
    // updated(){
    //     console.log("unmounted")
    // },
    methods:{
        finish(){
            clearInterval(this.timer)
            this.showBlock=false
            this.$emit("finish",this.reactionTime)
        }
    }
    
}
</script>

<style scoped>

.block{
    height:600px;
    width:650px;
    background-color: rgb(41, 170, 127);
    color: white;
    margin: auto;
    padding: auto;
}

p{
    margin: auto;
    justify-content: center;
    font-size: 50px;
    position: absolute;
    top: 45%;
    left: 43%;

}
</style>