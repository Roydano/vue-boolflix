<template>
  <main>
        <h3 v-if="searching != ''">Ricerca effettuata per {{searching}}</h3>

        <div class="movie">
            <h4>Movie</h4>
            <div v-for="movie in movieArray" :key="movie.id" class="card_movie">
                <div v-if="movie.poster_path != null" class="img_card">
                    <img :src='imgUrl + movie.poster_path' alt="">
                </div>
                <div v-else>senza copertina</div>
                <div class="card">
                    <p>Titolo: {{movie.title}}</p>
                    <p>Titolo in originale: {{movie.original_title}}</p>
                    <p>Lingua: {{movie.original_language}} <img :src="'https://www.countryflags.io/' + changeIdLang(movie.original_language) + '/flat/64.png'" :alt='movie.original_language' class="flag"></p>
                    <p>Voto: {{movie.vote_average}}</p>
                </div>
            </div>
        </div>
        
        <div class="series">
            <h4>Tv Series</h4>
            <div v-for="series in seriesArray" :key="series.id" class="card-serie">
                <div class="img_card">
                    <img :src='imgUrl + series.poster_path' alt="">
                </div>
                <div class="card">
                    <p>Titolo: {{series.name}}</p>
                    <p>Titolo in originale: {{series.original_name}}</p>
                    <p>Lingua: {{series.original_language}} <img :src="'https://www.countryflags.io/' + changeIdLang(series.original_language) + '/flat/64.png'" :alt='series.original_language' class="flag"></p>
                    <p>Voto: {{series.vote_average}}</p>
                    
                </div>
            </div>
            
        </div>
  </main>
</template>

<script>
export default {
    name: 'Main',
    props:['movieArray', 'seriesArray', 'searching'],

    data(){
        return{
            imgUrl: 'https://image.tmdb.org/t/p/w342/'

        }
    },

    methods:{
        changeIdLang( lang ){
            if( lang == 'en' ) return "gb";
            if( lang == 'ja' ) return "jp";

            return lang;
        }
    }

}
</script>

<style lang="scss" scoped>
    .flag{
        width: 2%;
    }

</style>