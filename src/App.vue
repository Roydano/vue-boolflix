<template>
  <div id="app">
    <Header @search="getMovie"/>
    <Main :movieArray="movieArray"/>

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
      movieArray:[],
      textSearch:''

    }
  },

  methods:{

    getMovie(searchText){
      this.textSearch = searchText

      axios
        .get(this.urlApi, {
          params:{
            api_key: 'c81548416aaaa14e591c85d4db9fdc1e',
            language: 'it-IT',
            query: this.textSearch
          }
        })
        .then(response => {
          console.log(response.data.results);
          this.movieArray = response.data
          // console.log(this.movieArray);
        })
        .catch(error =>{
          console.log('Errore ', error);
        })
    }

  }
}

</script>

<style lang="scss">

@import '@/style/common.scss';


</style>
