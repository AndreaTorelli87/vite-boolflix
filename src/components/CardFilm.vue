<script>
export default {
   name: "CardFilm",
   props: {
      image: String,
      title: String,
      originalTitle: String,
      language: String,
      vote: Number,
      overview: String
   }, methods: {
      flag(lingua) {

         if(lingua == "EN"){
            lingua = "GB"
         } else if(lingua == "JA"){
            lingua = "JP"
         } else if(lingua == "KO"){
            lingua = "KR"
         } else if(lingua == "ZH"){
            lingua = "CN"
         } else if(lingua == "HI"){
            lingua = "IN"
         } else if(lingua == "FA"){
            lingua = "IR"
         } else if(lingua == "TA"){
            lingua = "IN"
         } else if(lingua == "UR"){
            lingua = "PK"
         } else if(lingua == "TE"){
            lingua = "IN"
         } else if(lingua == "CS"){
            lingua = "CZ"
         } else if(lingua == "JV"){
            lingua = "ID"
         } else if(lingua == "DA"){
            lingua = "DK"
         } else if(lingua == "EL"){
            lingua = "GR"
         }

         return `https://flagsapi.com/${lingua}/flat/48.png`
      }
   }
}
</script>

<template>
   <div class="flip-card">
      <div class="flip-card-inner h-100 w-100 position-relative">
         <div class="flip-card-front h-100 w-100 position-absolute bg-warning">
            <div v-if="image == null" class="text-center">
               <h2 class="text-center p-3 fw-bold"> {{ title.toUpperCase() }} </h2>
               <span>Locandina non trovata</span>
            </div>
            <img :src="`https://image.tmdb.org/t/p/w342${image}`" :alt="title" class="w-100 h-100" v-else>
         </div>
         <div class="flip-card-back h-100 w-100 position-absolute bg-black text-white overflow-scroll text-center p-2">
            <h4 class="fw-bold">{{ title }}</h4>
            <h5 v-if="title != originalTitle" class="text-warning">{{ originalTitle }}</h5>
            <img 
               :src="flag(language)"
               :alt="`Lingua: ${language}`" 
               />
            <p>Voto: {{ vote }}</p>
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
   transition: transform 0.3s;
   transform-style: preserve-3d;
}
.flip-card-front, .flip-card-back {
   backface-visibility: hidden;
}
.flip-card:hover .flip-card-inner, .flip-card-back {
   transform: rotateX(180deg);
}
</style>