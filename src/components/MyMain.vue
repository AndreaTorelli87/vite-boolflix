<script>
import { store } from '../store.js';
import CardFilm from "./CardFilm.vue"

export default {

   components: {
      CardFilm
   },

   data() {
      return {
         store,
      }
   }
}

</script>

<template>
   <div class="container">
      <div class="row">
         <div class="col-3" v-for="(card, index) in store.filmListApi.results" :key="index">
            <CardFilm
               :image="card.poster_path"
               :title="card.title"
               :originalTitle="card.original_title"
               :language="card.original_language"
               :vote="card.vote_average"
               :overview="card.overview"
            />
         </div>
      </div>
   </div>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss';
</style>