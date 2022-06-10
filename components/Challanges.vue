<template>
    <div class="challenge-page">
        <p v-if="$fetchState.pending">Fetching challenges...</p>
        <p v-else-if="$fetchState.error">An error occurred :(</p>
        <div v-else class="challenge-container">
             
            <Challenge v-for="challenge in challenges.challenges" :key="challenge" :challenge="challenge"/>
        </div>
        
    </div>
</template>

<script>
export default {
    props:{
        sumname:''
    },
    data() {
        return {
            challenges: {},
            
        };
    },
    async fetch() {
        this.challenges = await fetch(
            `https://challenges-back-bmelectro.vercel.app/getchallenges?sumname=${this.sumname}`
        )
        .then((res) => res.json())
    },
    methods: {
        getBorderColor(level){
            switch (level) {
                case 'IRON':
                    return 'iron'
                    break;
            
                default:
                    break;
            }
        },

    },
    // watch: {
    //     sumname:function(){
    //         clearTimeout(this.timeout)
    //         this.timeout = setTimeout(()=>{this.$fetch()},100)
            
    //     }
    // },
};
</script>

<style>
</style>
