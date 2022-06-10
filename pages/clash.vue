<template>
  <main>
    <Nav/>
    <h1>Clash Checker</h1>
    <h3>Enter a summoner name to check if he and his current clash team played any games together before</h3>
    <input type="text" placeholder="Enter Summoner Name" spellcheck="false" @keydown="lookupClash" v-model="sumname">
    <ClashContainer :sumName="sumname" v-if="showClash"/>
  </main>
</template>

<script>
export default {
    data(){
        return{
            sumname:'',
            showClash: false
        }
    },
    methods:{
        lookupClash(e){
            if(e.key === 'Enter'){
                this.showClash = false
                setTimeout(()=>{
                    this.showClash = true
                },50)
                
            }
        }
    }
}
</script>

<style>

</style>