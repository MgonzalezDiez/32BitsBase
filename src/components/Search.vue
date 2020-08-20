<template>
    <div>
      <p>Cantidad de juegos disponibles : {{games.length}}</p>
      <input type="text" placeholder="Buscar" v-model="search"/>
      <hr>
      <GameList :games='filterGames'/>
      
      <!-- <ul v-if="SearchById">
        <li>
          <b>{{ SearchById.nombre }} </b> 
        </li>
      </ul>  -->
    </div>
</template>
<script>

import {mapState, mapGetters } from 'vuex'
import GameList from './GameList'
export default {
  data() {
    return {
      search: null
    }
  },
  components:{
    GameList
  },
  computed: {
    ...mapState(["games"]),
    ...mapGetters(["findGame"]),
    filterGames() {
      if(this.search){
        return this.findGame(this.search)
      }else{
        return this.games
      }
    },
    availableGames(state)
    {
      return state.games.filter((game) =>
      {
        return game.stock > 0
      })
    }
  }
}
</script>