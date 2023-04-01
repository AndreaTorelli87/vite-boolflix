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
   <h1>H1 in MyHeader</h1>
   <div class="input-group">
      <input type="text" placeholder="Cerca..." v-model="store.input" @keyup.enter="$emit('cercaFilm')">
      <button @click="$emit('cercaFilm')">Cerca</button>
   </div>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss';
</style>