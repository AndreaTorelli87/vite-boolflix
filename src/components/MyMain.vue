<script>
import { store } from '../store.js';
import CardFilm from "./CardFilm.vue"
import CardTv from "./CardTv.vue"


export default {

   components: {
      CardTv,
      CardFilm
   },
   data() {
      return {
         store,
      }
   },
   computed: {
      // cambioLingua() {
      //    if (store.filmListApi.original_language == en) {
      //       console.log(store.filmListApi)
      //    }
      // }
   }
}

</script>

<template>
   <!-- CONTENITORE PER I FILM -->
   <div class="container">
      <div class="row">
         <h1 class="text-center p-2" v-if="store.filmListApi.length == 0">Scegli un film</h1>
         <div class="col-3" v-for="(card, index) in store.filmListApi" :key="index">
            <CardFilm
               :image="card.poster_path"
               :title="card.title"
               :originalTitle="card.original_title"
               :language="card.original_language.toUpperCase()"
               :vote="card.vote_average"
               :overview="card.overview"
            />
         </div>
         <h1 v-if="store.filmListApi == 0">Non è stato trovato nessun film</h1>
      </div>
   </div>
   <!-- CONTENITORE PER LE SERIE TV -->
   <div class="container">
      <div class="row">
         <h2>SERIE TV!!!!!!!!!!!!!!!!!!!!!!!!!</h2>
         <div class="col-3" v-for="(card, index) in store.tvListApi" :key="index">
            <CardTv
               :image="card.poster_path"
               :name="card.name"
               :originalName="card.original_name"
               :language="card.original_language.toUpperCase()"
               :vote="card.vote_average"
               :overview="card.overview"
            />
         </div>
         <h1 v-if="store.filmListApi == 0">Non è stata trovata nessuna serie tv</h1>
      </div>
   </div>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss';
</style>