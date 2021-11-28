<template>
    <div id="card_container">
        <img :src="details.poster" alt="">
        <h1>{{details.title}}</h1>
        <p>{{details.author}}</p>
        <p>{{details.year}}</p>
    </div>
</template>

<script>
export default {
    name: 'Disclist',
    props:{
       details:Object,
    }
}
</script>

<style>
#card_container{
    color: #ffffff;
    background-color:#2e3a46;
    margin: 10px;
    width: 150px;
    display: flex;
    flex-direction: column;
    padding: 20px;
}
#card_container img{
    width: 100%;
}
</style>