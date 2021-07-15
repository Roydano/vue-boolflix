<template>
  <main class="container">

        <div v-if="searching == ''">
            <div v-if="idSelect == ''">
                <h2 class="text-center">Titoli del momento</h2>
                <div class="desk d-flex flex-wrap justify-content-center mb-5">
                    <Card v-for="movie in trendArray" :key="movie.id" :movie="movie" class="p-2"/>
                </div>
            </div>

            <div v-else>
                <div v-for="name in genreArray" :key="name.id">
                   <h2 class="text-center" v-if="name.id == idSelect">{{name.name}}</h2>
                </div>
                <span>{{seriesArray}}</span>
            </div>
        </div>

        <div v-else>
            <h3 class="mt-3 grey" v-if="searching != ''">Ricerca effettuata per: <span>{{searching}}</span></h3>

            <!--START FILM SECTION -->
            <h4 class="text-center my-3">Movie</h4>
            <div class="desk d-flex flex-wrap justify-content-center mb-5">
                <Card v-for="movie in movieArray" :key="movie.id" :movie="movie" class="card-series m-1"/>
            </div>
            <!--END FILM SECTION -->

        
            <!-- START TV SERIES SECTION -->
            <h4 class="text-center my-3">Tv Series</h4>
            <div class="desk d-flex flex-wrap justify-content-center mb-5">
                <Card v-for="movie in seriesArray" :key="movie.id" :movie="movie" class="card-series m-1"/>
            </div>
            <!-- END TV SERIES SECTION -->
        </div>

  </main>
</template>

<script>
import Card from '@/components/Card.vue';

export default {
    name: 'Main',
    props:['movieArray', 'seriesArray', 'searching', 'trendArray', 'idSelect', 'genreArray'],

    data(){
        return{
            filterArray:''
        }
    },

    components:{
        Card,
    },

}
</script>

<style lang="scss" scoped>

    h4,
    span,
    h2{
        color: red;
    }

    .grey{
        color: rgb(97, 97, 97);
    }

    h1{
        color: white;
    }
    

    

</style>


