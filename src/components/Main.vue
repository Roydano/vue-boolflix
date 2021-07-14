<template>
  <main class="container">
        <h3 class="mt-3" v-if="searching != ''">Ricerca effettuata per {{searching}}</h3>

        <!--START FILM SECTION -->
        <h4 class="text-center my-3">Movie</h4>

        <div class="desk d-flex flex-wrap justify-content-center mb-5">
            <Card v-for="movie in movieArray" :key="movie.id" :movie="movie" class="card_movie m-1"/>
            <!-- <div v-for="movie in movieArray" :key="movie.id" class="card_movie m-1"> -->
                <!-- START POSTER FILM -->
                <div v-if="movie.poster_path != null" class="img_card">
                    <img :src='imgUrl + movie.poster_path' alt="">
                    <!-- START FILM DETAILS -->
                    <div class="card">
                        <p>Titolo: {{movie.title}}</p>
                        <p>Titolo in originale: {{movie.original_title}}</p>
                        <p>Lingua: {{movie.original_language}} <img :src="'https://www.countryflags.io/' + changeIdLang(movie.original_language) + '/flat/64.png'" :alt='movie.original_language' class="flag"></p>
                        <p>Voto: {{movie.vote_average}}</p>

                        <!-- STAR VOTE -->
                        <div class="star">
                            <i class="fas fa-star" :class="movie.vote_average > 1 ? 'red' : 'grey'"></i>
                            <i class="fas fa-star" :class="movie.vote_average >= 4 ? 'red' : 'grey'"></i>
                            <i class="fas fa-star" :class="movie.vote_average >= 6 ? 'red' : 'grey'"></i>
                            <i class="fas fa-star" :class="movie.vote_average >= 8 ? 'red' : 'grey'"></i>
                            <i class="fas fa-star" :class="movie.vote_average > 9 ? 'red' : 'grey'"></i>
                        </div>
                    </div>
                    <!-- END FILM DETAILS -->
                </div>

                <div v-else class="unknown img_card">
                    <h4>{{movie.title}}</h4>
                    <div class="card">
                        <p>Titolo: {{movie.title}}</p>
                        <p>Titolo in originale: {{movie.original_title}}</p>
                        <p>Lingua: {{movie.original_language}} <img :src="'https://www.countryflags.io/' + changeIdLang(movie.original_language) + '/flat/64.png'" :alt='movie.original_language' class="flag"></p>
                        <p>Voto: {{movie.vote_average}}</p>

                        <!-- STAR VOTE -->
                        <div class="star">
                            <i class="fas fa-star" :class="movie.vote_average > 1 ? 'red' : 'grey'"></i>
                            <i class="fas fa-star" :class="movie.vote_average >= 4 ? 'red' : 'grey'"></i>
                            <i class="fas fa-star" :class="movie.vote_average >= 6 ? 'red' : 'grey'"></i>
                            <i class="fas fa-star" :class="movie.vote_average >= 8 ? 'red' : 'grey'"></i>
                            <i class="fas fa-star" :class="movie.vote_average > 9 ? 'red' : 'grey'"></i>
                        </div>
                    </div>
                    <!-- END FILM DETAILS -->

                </div>
                <!-- END POSTER FILM -->

                
            <!-- </div> -->
        </div>
        <!-- END FILM SECTION -->
        
        <!-- START TV SERIES SECTION -->
        <h4 class="text-center my-3">Tv Series</h4>

        <div class="desk d-flex flex-wrap justify-content-center">
            <div v-for="series in seriesArray" :key="series.id" class="card-series m-1">

                <!-- START POSTER TV SERIES -->
                <div v-if="series.poster_path != null" class="img_card">
                    <img :src='imgUrl + series.poster_path' alt="">
                </div>
                <div v-else class="unknown">{{series.title}}</div>
                <!-- END POSTER TV SERIES -->

                <!-- START TV SERIES DETAILS -->
                <div class="card d-none">
                    <p>Titolo: {{series.name}}</p>
                    <p>Titolo in originale: {{series.original_name}}</p>
                    <p>Lingua: {{series.original_language}} <img :src="'https://www.countryflags.io/' + changeIdLang(series.original_language) + '/flat/64.png'" :alt='series.original_language' class="flag"></p>
                    <p>Voto: {{series.vote_average}}</p>

                    <!-- STAR VOTE -->
                    <div class="star">
                        <i class="fas fa-star" :class="series.vote_average > 1 ? 'red' : 'grey'"></i>
                        <i class="fas fa-star" :class="series.vote_average >= 4 ? 'red' : 'grey'"></i>
                        <i class="fas fa-star" :class="series.vote_average >= 6 ? 'red' : 'grey'"></i>
                        <i class="fas fa-star" :class="series.vote_average >= 8 ? 'red' : 'grey'"></i>
                        <i class="fas fa-star" :class="series.vote_average > 9 ? 'red' : 'grey'"></i>
                    </div>
                    
                </div>
                <!-- END TV SERIES DETAILS -->

            </div>
        </div>
        <!-- END TV SERIES SECTION -->

  </main>
</template>

<script>
import Card from '@/components/Card.vue';

export default {
    name: 'Main',
    props:['movieArray', 'seriesArray', 'searching'],

    components:{
        Card
    },

    data(){
        return{
            imgUrl: 'https://image.tmdb.org/t/p/w342/', 

        }
    },

    methods:{
        changeIdLang( lang ){
            if( lang == 'en' ) return "gb";
            if( lang == 'ja' ) return "jp";

            return lang;
        },

    }

}
</script>

<style lang="scss" scoped>

    .img_card{
        position: relative;
        height: 450px;
        width: 300px;
        background-color: yellow;
        border: 2px solid black;
        
        &:hover .card{
            display: block;
        }
        

        img{
            height: 100%;
            width: 100%;
        }

        .card{
            display: none;
            height: 450px;
            width: 300px;
            background-color: yellow;
            border: 2px solid black;
            position: absolute;
            top: 0;
            left: 0;

            .flag{
            width: 10%;
            }

            .red{
            color: red;
            }
        }
    }

    .unknown{
        height: 450px;
        width: 300px;
        background-color: rgb(59, 59, 59);
        border: 2px solid black;
    }
    
    

</style>