<script>
export default {
   name: "CardTv",
   props: {
      image: String,
      name: String,
      originalName: String,
      language: String,
      vote: Number,
      overview: String
   }, methods: {
      flag(lingua) {
         let converti= [];
         converti["EN"] = "GB";
         converti["JA"] = "JP";
         converti["KO"] = "KR";
         converti["ZH"] = "CN";
         converti["HI"] = "IN";
         converti["FA"] = "IR";
         converti["TA"] = "IN";
         converti["UR"] = "PK";
         converti["TE"] = "IN";
         converti["CS"] = "CZ";
         converti["JV"] = "ID";
         converti["DA"] = "DK";
         converti["EL"] = "GR";
         lingua = converti[lingua]!="" ? lingua : converti[lingua];
         return `https://flagsapi.com/${lingua}/flat/48.png`
      },
      votoStelle(voto){
         return voto*10; 
      }
   }
}
</script>

<template>
   <div class="flip-card">
      <div class="flip-card-inner h-100 w-100 position-relative">
         <div class="flip-card-front h-100 w-100 position-absolute bg-warning">
            <div v-if="image == null" class="text-center">
               <h2 class="text-center p-3 fw-bold"> {{ name.toUpperCase() }} </h2>
               <span>Locandina non trovata</span>
            </div>
            <img :src="`https://image.tmdb.org/t/p/w342${image}`" :alt="name" class="w-100 h-100" v-else>
         </div>
         <div class="flip-card-back h-100 w-100 position-absolute bg-black text-white overflow-scroll text-center p-2">
            <h4 class="fw-bold">{{ name }}</h4>
            <h5 v-if="name != originalName" class="text-warning">{{ originalName }}</h5>
            <img 
               :src="flag(language)"
               :alt="`Lingua: ${language}`" 
               />
            <!-- <p>Voto: {{ vote }}</p> -->
            <div class="stars-outer fs-3">
               <div class="stars-inner fs-3" :style="width: votoStelle(vote)"></div>
            </div>
            <!-- <h1>{{ votoStelle(vote) }}</h1> -->
            <p>{{ overview }}</p>
         </div>
      </div>
   </div>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss';

.stars-outer {
  display: inline-block;
  position: relative;
  content: "\2605 \2605 \2605 \2605 \2605";
  &:before {
}
}

.stars-inner {
  position: absolute;
  top: 0;
  left: 0;
  white-space: nowrap;
  overflow: hidden;
//   width: 55%;

  &::before {
  content: "\2606 \2606 \2606 \2606 \2606";
  color: #f8ce0b;
}
}

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