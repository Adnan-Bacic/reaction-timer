<template>
  <div class="block" v-if="showBlock" v-on:click="stopTimer">
      click me
  </div>
</template>

<script>
export default {
    props: ['delayAmount'],
    data(){
        return{
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted(){
        console.log('mounted')
        //show the block after a delay prop from app.vue
        setTimeout(() => {
            console.log('delayamount', this.delayAmount)

            this.showBlock = true
            this.startTimer()
        }, this.delayAmount);
    },
    updated(){
        console.log('updated')
    },
    unmounted(){
        console.log('unmounted')
    },
    methods:{
        startTimer(){
            //increase by 10 every 10 milisec
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer(){
            console.log(this.reactionTime)
            clearInterval(this.timer)

            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
  .block {
    width: 400px;
    border-radius: 20px;
    background:  #0faf87;;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>