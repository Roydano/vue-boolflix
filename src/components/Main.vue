<template>
  <main class="container">
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
   

}
</script>

<style lang="scss" scoped>

    h4,
    span{
        color: red;
    }

    .grey{
        color: rgb(97, 97, 97);
    }

    

</style>