<template>
  <p>{{ playerScore }}</p>
  <p class="rank">Rank: {{ rank }}</p>
</template>

<script>
export default {
    name: 'Results',
    props: ['playerScore'],
    data(){
        return{
            rank: null
        }
    },
    mounted(){
        if(this.playerScore < 250){
            this.rank = 'S'
        } else if(this.playerScore < 400){
            this.rank = 'A'
        } else {
            this.rank = 'B'
        }
    }
}
</script>

<style>
  .rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
  }
</style>