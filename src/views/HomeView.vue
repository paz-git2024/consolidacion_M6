<template>
  <div>
     <h1>Home - Opiniones sobre Juegos</h1>
  <div>
    <CardList :games="games"></CardList>
  </div>
  </div>
</template>

<script>
import CardList from '@/components/CardList.vue';

export default {
  name:'HomeView' ,
    components: {
      CardList
    }
  ,
  // props: {},
  data: function(){
    return {
      games:[]
    }
  },
  data2(){
    return{
      games: []
    }
  },
  // computed: {},
  methods: {
   async fetchGames(){
      const API_KEY="f4c3ea92f06841b9aad525179ce39ddb"
      const url=`https://api.rawg.io/api/games?key=${API_KEY}`;
      const response=await fetch(url) 
      const data=await response.json() 
      console.log(data)
      this.games=data.results
    },
     opinar(nombreJuego) {
      this.$router.push({ name: 'opiniones', params: { juego: nombreJuego } });
    }
  },

  
  // watch: {},
  // components: {},
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  created() {
    this.fetchGames()
  }
  // -- End Lifecycle Methods
}
</script>

<style scoped >
  .home {
    padding:20px
  }
</style> 