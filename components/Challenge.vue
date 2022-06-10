<template>
    <div class="challenge">
        <span class="border-color" :class="challenge.level"></span>
        <div class="challenge-info-container">
            <div class="challenge-info"><span>{{challenge.challengeId}}</span><span :class="'level'+challenge.level">{{challenge.level}}</span></div>
            <span class="challenge-text">{{challenge.challengeText}}</span>
            <div class="threshhold-container"><div class="threshold"></div>{{getThreshholdText(challenge.thresholds, challenge.value, challenge.level)}}</div>
        </div>
    </div>
</template>

<script>
export default {
    props:{
        challenge:{}
    },
    methods:{
        getThreshholdText(thresholds, value, level){
            switch (level) {
                case 'Iron':
                    return `${value}/${thresholds['BRONZE']}`
                case 'BRONZE':
                    return `${value}/${thresholds['SILVER']}`
                case 'SILVER':
                    return `${value}/${thresholds['GOLD']}`
                case 'GOLD':
                    return `${value}/${thresholds['PLATINUM']}`
                case 'PLATINUM':
                    return `${value}/${thresholds['DIAMOND']}`
                case 'DIAMOND':
                    return `${value}/${thresholds['MASTER']}`
                case 'MASTER':
                    return `${value}/${thresholds['GRANDMASTER']}`
                case 'GRANDMASTER':
                    return `${value}/${thresholds['CHALLENGER']}`
                case 'CHALLENGER':
                    return `${value}/${thresholds['CHALLENGER']}` 
                default:
                    break;
            }

            
        }
    }
}
</script>

<style>

</style>