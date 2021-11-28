<template>
  <section>
    <header>
      <nav>
        <img :src=" require('@/assets/logo-spotify.png')" alt="Logo">
      </nav>
    </header>
    <main>
      <div id="box">
        <div id="card_container1">
          <Disclist
          v-for ="cd,i in lista" 
          :key="i"
          :details="cd"
          />
        </div>
      </div>
    </main>
  </section>
</template>

<script>
import axios from "axios";
import Disclist from '@/components/Disclist.vue'
export default {
   name:'Main',
    components: {
    Disclist
  },
  data(){
    return{
      apiUrl:"https://flynn.boolean.careers/exercises/api/array/music",
      lista: [],      
    }
  },
  created(){
    this.getCharachters();
  },
  methods:{
    getCharachters(){
      axios
      .get(this.apiUrl)
      .then((result) => {
        this.lista = result.data.response;
      })
    }
  }
}
</script>

<style scoped lang="scss">

  img{
    width:70px;
    display: flex;
    padding:8px;
  }

  nav{
    background-color:#2e3a46;
    height: 10vh;
    padding: 10px;
    margin-top:-70px;
  }

  main{
    display: flex;
    flex-wrap:wrap;
    background-color:#1e2d3b;
  }

  #card_container1{
    display: flex;
    flex-wrap: wrap;
  }

  #box{
    width: 70%;
    margin: 0 auto;
  }

</style>




