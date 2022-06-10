<template>
    <main>
        <Nav/>
        <h1>Welcome to challenge planner</h1>
        <h2>Here you can create a team and keep track of your premade challenges</h2>
        <input type="text" placeholder="Enter team name" spellcheck="false" @keydown="createTeam" v-model="teamName">

        <div>
        </div>
    </main>
   
    
</template>

<script>
export default {
    data(){
        return{
            teamName:''
        }
    },
    methods:{
            createTeam(e){
                console.log(e)
                if(e.key === 'Enter'){
                    
                }
            }
    }
}
</script>

<style>

</style>