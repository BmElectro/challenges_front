<template>
  <div class="game-container">
    <div class="game-mini" v-if="!expand">
            <span>{{gameData.gameMode}}</span>
            <div>
                <div>
                    <span v-for="player in blueTeam" :key="player">
                        <span v-if="allNames.includes(player.sumName)" class="player-name">{{player.sumName}}</span>
                        <span v-else class="player-name red-player-name" title="RED: Player is not part of the current Clash Team of the searched summoner">{{player.sumName}}</span>
                        <span class="player-champ">{{player.champ}}</span>
                        <span class="player-kda">{{player.kda.kills}}<span class="kda-separator">/</span>{{player.kda.deaths}}<span class="kda-separator">/</span>{{player.kda.assists}}</span>
                    </span>
                </div>
                <div>
                    <span v-for="player in redTeam" :key="player">
                        <span v-if="allNames.includes(player.sumName)" class="player-name">{{player.sumName}}</span>
                        <span v-else class="player-name red-player-name" title="RED: Player is not part of the current Clash Team of the searched summoner">{{player.sumName}}</span>
                        <span class="player-champ">{{player.champ}}</span>
                        <span class="player-kda">{{player.kda.kills}}<span class="kda-separator">/</span>{{player.kda.deaths}}<span class="kda-separator">/</span>{{player.kda.assists}}</span>
                    </span>
                </div>
            </div>
            
    </div>
    <div class="game-large" v-else>

    </div>
  </div>
</template>

<script>
export default {
    props:{
        gameData:{},
        allNames:[]
    },
    data(){
        return{
            expand:false
        }
    },
    computed:{
        blueTeam: function(){
            let blueTeam = []
            for(let p of this.gameData.participants){
                if(p.teamId == 100){
                    blueTeam.push({
                        sumName: p.summonerName,
                        kda:{kills:p.kills, deaths:p.deaths, assists:p.assists},
                        champ:p.championName,
                    })
                }
            }
            return blueTeam
        },
        redTeam:function(){
            let redTeam = []
            for(let p of this.gameData.participants){
                if(p.teamId != 100){
                    redTeam.push({
                        sumName: p.summonerName,
                        kda:{kills:p.kills, deaths:p.deaths, assists:p.assists},
                        champ:p.championName,
                    })
                }
            }
            return redTeam
        }
    }

}
</script>

<style>

</style>