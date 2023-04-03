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
      urlApi += store.input.replace(" ", "+")

      axios.get(urlApi).then(response => {
        this.store.filmListApi = response.data.results;
      });

      let urlApiTv = 'https://api.themoviedb.org/3/search/tv?api_key=2d6841a37fd674dfe6e37d212e5b383a&language=it_IT&query='
      urlApiTv += store.input.replace(" ", "+")

      axios.get(urlApiTv).then(response => {
        this.store.tvListApi = response.data.results;
        });
      // console.log("ciaone")
      // console.log(store.filmListApi)
    },
    // getTv() {
    //   console.log("ciaone")

    // let urlApiTv = 'https://api.themoviedb.org/3/search/tv?api_key=2d6841a37fd674dfe6e37d212e5b383a&language=it_IT&query='
    // urlApiTv += store.input.replace(" ", "+")

    // axios.get(urlApiTv).then(response => {
    //   this.store.tvListApi = response.data.results;
    // });


    // // console.log("ciaone")
    // // console.log(store.filmListApi)
    // }
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
