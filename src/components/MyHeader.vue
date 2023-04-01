<script>
import { store } from '../store.js';

export default {

   data() {
      return {
         store,
      }
   },
   methods: {

   }
}


</script>

<template>
   <div class="bg-danger">
      <div class="container p-5">
         <div class="input-group mb-3">
            <input type="text" class="form-control" placeholder="Cerca..." aria-label="Cerca..." aria-describedby="button-addon2" v-model="store.input" @keyup.enter="$emit('cercaFilm')">
            <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="$emit('cercaFilm')">Cerca</button>
         </div>
      </div>
   </div>   
</template>

<style lang="scss" scoped>
@use '../styles/general.scss';
</style>