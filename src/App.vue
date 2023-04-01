<script>
import axios from 'axios';
import { store } from './store.js';
import MyHeader from './components/MyHeader.vue';
import MyMain from './components/MyMain.vue';
import CardFilm from './components/CardFilm.vue';


export default {
  components: {
    MyHeader,
    MyMain,
    CardFilm,

  },
  data() {
    return {
      store,
    }
  },
  methods: {
    getFilm() {

      let urlApi = 'https://api.themoviedb.org/3/search/movie?api_key=2d6841a37fd674dfe6e37d212e5b383a&language=it-IT&query=';



        console.log("è entrato nel IF")
        urlApi += store.input.replace(" ", "+")

      console.log(urlApi.length);

      axios.get(urlApi)
        .then(response => {
          this.store.filmListApi = response.data;
          console.log(this.store.filmListApi)
        });
    },
  }
}

</script>

<template>
  <MyHeader @cercaFilm="getFilm" />
  <MyMain></MyMain>
</template>

<style lang="scss">
@use './styles/general.scss';
</style>
