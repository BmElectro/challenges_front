<template>
  <div class="clash-container">
    <p v-if="$fetchState.pending">Fetching games...</p>
    <p v-else-if="$fetchState.error">An error occurred :(</p>
    <Game v-else v-for="game in games.details" :key="game" :gameData="game" :allNames="games.allNames"/>
  </div>
</template>

<script>
export default {
    props:{
        sumName:''
    },
    data(){
        return{
            games:{}
        }
    },
    async fetch() {
        this.games = await fetch(
            `https://challenges-back-bmelectro.vercel.app/clash/?sumname=${this.sumName}`
        )
        .then((res) => res.json())
    },
}
</script>

<style>

</style>