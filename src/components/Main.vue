<template>
  <section>
    <header>
      <nav>
        <img :src=" require('@/assets/logo-spotify.png')" alt="Logo">
      </nav>
    </header>
    <main>
      <div id="box">
        <Search @selezionato="cambioGenere" />
        <div id="card_container1">
          <Disclist
          v-for ="cd,i in filteredListaCd" 
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
import Disclist from '@/components/Disclist.vue';
import Search from '@/components/Search.vue';
export default {
   name:'Main',
    components: {
    Disclist,
    Search,
  },
  data(){
    return{
      apiUrl:"https://flynn.boolean.careers/exercises/api/array/music",
      lista: [],
      genere: null,
      testo:''
      // Rock:[0,5,6],
      // Pop:[1,2,9],
      // Jazz:[3,8],
      // Metal:[4,7],
      // cardchoosen:"",
    }
  },
  created(){
    this.getCharachters();
  },

  computed:{
    filteredListaCd(){
      if( this.genere === null )
        return this.lista
      
      return this.lista.filter( (disco) => {
        return disco.genre === this.genere ;
      })
    }

  },
  methods:{
    cambioGenere(genere){
      this.genere = genere;
    },
    getCharachters(){
      axios
      .get(this.apiUrl)
      .then((result) => {
        this.lista = result.data.response;
      })
    },
    searching(){
      this.cardchoosen = this.Rock
      console.log(this.cardchoosen);
    },
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

  form{
    padding:20px;
    color:white
  }

</style>




