<script>
// import { store } from '../store.js';
export default {

   name: "CardFilm",
   props: {
      image: String,
      title: String,
      originalTitle: String,
      language: String,
      vote: String,
      overview: String
   }
}


</script>

<template>
   <div class="flip-card">
      <div class="flip-card-inner h-100 w-100 position-relative">
         <div class="flip-card-front h-100 w-100 position-absolute bg-warning">
            <img :src="`https://image.tmdb.org/t/p/w342${image}`" :alt="title" class="w-100 h-100">
         </div>
         <div class="flip-card-back h-100 w-100 position-absolute bg-black text-white overflow-scroll text-center p-2">
            <h4>{{ title }}</h4>
            <h5 v-if="title != originalTitle">{{ originalTitle }}</h5>
            <p>{{ language }}</p>
            <p>{{ vote }}</p>
            <p>{{ overview }}</p>
         </div>
      </div>
   </div>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss';

.flip-card {
   width: 332px;
   height: 503px;
   perspective: 1000px;
}
.flip-card-inner {
   transition: transform 0.6s;
   transform-style: preserve-3d;
}
.flip-card-front, .flip-card-back {
   backface-visibility: hidden;
}
.flip-card:hover .flip-card-inner, .flip-card-back {
   transform: rotateY(180deg);
}
</style>