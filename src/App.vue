<template>
  <div id="app">
    <Header @search="getMovie"/>
    <Main :movieArray="movieArray" :seriesArray="seriesArray" :searching="textSearch"/>

  </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue';
import Main from '@/components/Main.vue';


export default{
  name: 'App',

  components:{
    Header,
    Main
  },

  data(){
    return{
      urlApi: 'https://api.themoviedb.org/3/search/movie?',
      urlApiSeries: 'https://api.themoviedb.org/3/search/tv?',
      movieArray:[],
      seriesArray:[],
      textSearch: ''

    }
  },

  methods:{

    getMovie(searchText){
      this.textSearch = searchText

      // chiamata film
      axios
        .get(this.urlApi, {
          params:{
            api_key: 'c81548416aaaa14e591c85d4db9fdc1e',
            language: 'it-IT',
            query: this.textSearch
          }
        })
        .then(response => {
          // console.log(response.data.results);
          this.movieArray = response.data.results
          // console.log(this.movieArray);
        })
        .catch(error =>{
          console.log('Errore ', error);
        })

      //chiamata serie tv
      axios
        .get(this.urlApiSeries, {
          params:{
            api_key: 'c81548416aaaa14e591c85d4db9fdc1e',
            language: 'it-IT',
            query: this.textSearch
          }
        })
        .then(response => {
          // console.log(response.data.results);
          this.seriesArray = response.data.results
          // console.log(this.movieArray);
        })
        .catch(error =>{
          console.log('Errore ', error);
        })

        console.log(this.textSearch);
    }

  }
}

</script>

<style lang="scss">

@import '@/style/common.scss';


</style>
