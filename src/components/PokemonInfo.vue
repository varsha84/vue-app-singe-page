<template>
    <div class="info-list">
        <h3>{{title}}</h3> 
        <ul>
            <li v-for="item in items"  :key="item">{{item}}</li>
        </ul>
    </div>
</template>

<script>

export default {
    name: "PokemonInfo",
    props : {
        title: String,
        items: Array,
    }
}

</script>


<style scoped>

h3, ul{
    text-align:left;
}
h3{
    padding-left: 15px;
}

</style>