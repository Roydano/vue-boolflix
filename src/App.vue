<template>
  <div id="app">
    <Header @search="getMovie"/>
    <Main :movieArray="movieArray" :seriesArray="seriesArray" :searching="textSearch" :trendArray="trendArray"/>

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
      urlApiMovie: 'https://api.themoviedb.org/3/search/movie?',
      urlApiSeries: 'https://api.themoviedb.org/3/search/tv?',
      movieArray:[],
      seriesArray:[],
      trendArray:[],
      textSearch: '',

    }
  },

  created(){
    this.trendFilm()
  //  console.log(this.trendArray)
    
  },

  methods:{

    trendFilm(){
      axios
        .get('https://api.themoviedb.org/3/trending/all/day?api_key=c81548416aaaa14e591c85d4db9fdc1e&language=it-IT')
         .then(response => {
           // console.log(response.data.results);
           this.trendArray = response.data.results
          //  console.log(this.trendArray);
         })
         .catch(error =>{
           console.log('Errore ', error);
        })

        
    },

    getMovie(searchText){
      this.textSearch = searchText
      const params = {
        params:{
            api_key: 'c81548416aaaa14e591c85d4db9fdc1e',
            language: 'it-IT',
            query: this.textSearch
          }
      }

      //! METODODI CHIAMATA AXIOS CHE COMPRENDE PIU'
      axios
        .all([
          axios.get(this.urlApiMovie, params),
          axios.get(this.urlApiSeries, params)
        ])
        .then(axios.spread((responseMovie, responseSeries) =>{
          this.movieArray = responseMovie.data.results;
          this.seriesArray = responseSeries.data.results
        }))
        .catch(axios.spread((errorMovie, errorSeries) =>{
          console.log('Errore ', errorMovie);
          console.log('Errore ', errorSeries);

        }))


      //!METODO DI CHIAMATA AXIOS CLASSICO CON DUE CHIAMATE DISTINTE
      // // FILM CALL
      // axios
      //   .get(this.urlApi, {
      //     params:{
      //       api_key: 'c81548416aaaa14e591c85d4db9fdc1e',
      //       language: 'it-IT',
      //       query: this.textSearch
      //     }
      //   })
      //   .then(response => {
      //     // console.log(response.data.results);
      //     this.movieArray = response.data.results
      //     // console.log(this.movieArray);
      //   })
      //   .catch(error =>{
      //     console.log('Errore ', error);
      //   })

      // // TV SERIES CALL
      // axios
      //   .get(this.urlApiSeries, {
      //     params:{
      //       api_key: 'c81548416aaaa14e591c85d4db9fdc1e',
      //       language: 'it-IT',
      //       query: this.textSearch
      //     }
      //   })
      //   .then(response => {
      //     // console.log(response.data.results);
      //     this.seriesArray = response.data.results
      //     // console.log(this.movieArray);
      //   })
      //   .catch(error =>{
      //     console.log('Errore ', error);
      //   })

      //   console.log(this.textSearch);

    }

  }
}

</script>

<style lang="scss">

@import '@/style/common.scss';


</style>
