<template>
  <main>
      <Nav/>
      <h1>Challanges</h1>
      <input type="text" name="" id="" @keydown="getChallenges" v-model="summonerName" placeholder="Enter your summoner name" spellcheck="false">
      <Challanges :sumname="summonerName" v-if="showSummonerStats"/>
  </main>
</template>

<script>
export default {
  name: 'IndexPage',
  data(){
    return{
      summonerName:'',
      keyTimer:'',
      showSummonerStats: false
    }
  },
  methods:{
    // userTyping(e){
    //   this.showSummonerStats = false
    //   clearTimeout(this.keyTimer)
    //   this.keyTimer = setTimeout(()=> {
    //         if(this.summonerName != ''){
    //             this.showSummonerStats = true

    //         }
    //     }, 1500)
      

    // }
    getChallenges(e){
      if(e.key === 'Enter'){
        this.showSummonerStats = false
        this.showSummonerStats = true
      }
    }

  }
}
</script>
