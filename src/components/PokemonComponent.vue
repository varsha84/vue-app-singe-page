<template>
    
    <div class="container">
        <div class="images">
    
            <img @click="getPokemonData('ditto')"  name= "ditto" src="../assets/Ditto.jpg" alt="Italian Trulli">
            <img @click="getPokemonData('pikachu')" name= "pikachu" src="../assets/Pikachu.jpg"  alt="Italian Trulli">
            <img @click="getPokemonData('charmander')" name= "charmander" src="../assets/Charmander.jpg" alt="Italian Trulli">
        </div>
        <div class="info">
            <h1>{{name}}</h1>
            <div class="details"> 
                <PokemonInfo title="Abilitie" :items="abilities"></PokemonInfo>
                <PokemonInfo title="Stats" :items="stats"></PokemonInfo>
                <PokemonInfo title="Moves" :items="moves"></PokemonInfo>
            </div>
        </div>
    </div>
</template>

<script>
    import PokemonInfo from './PokemonInfo.vue'
    export default{
        name:'PokemonComponent',
        data : ()  => { 
            return {
                name : "",
                abilities: [],
                moves : [],
                stats: [],
        }
        },
        components:{
            PokemonInfo
        },
        methods: {
            async getPokemonData(value) {
            const userData =  await fetch(`https://pokeapi.co/api/v2/pokemon/${value}`);
            const result = await userData.json();
            console.log(result);
            this.name = value;
            this.abilities = result.abilities.map((item) => {return item.ability.name});
            this.moves = result.moves.map((item) => {return item.move.name});
            this.stats = result.stats.map((item) => {return item.stat.name});
            },
        
           
        },
        async created() {
            this.getPokemonData('pikachu');
        }
    }
    
</script>

<style scoped> 
    .container{
        height: auto;
        padding: 40px;
        background: rgb(61, 155, 199);
        
    }
    .images{
        display: flex;
        justify-content: space-between;
        margin-bottom: 40px;
    }
    img {
        width: 200px;
        height:200px;
        margin: 20px;
        border-radius: 50%;
        background: whitesmoke;
    }
   .details{
    display: flex;
    justify-content: space-around;
   }
   .info{
    background: whitesmoke;
    border-radius: 20px;
    padding: 10px;
    
   }


   @media only screen and (max-width: 600px) {
    .details{
     flex-direction: column;
   }
   .images{
    align-items: center;
    flex-direction: column;

   }
}
</style>