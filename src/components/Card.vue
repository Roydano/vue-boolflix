<template>
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
</template>

<script>
export default {
    name: 'Card',
    props: ['movie']

}
</script>

<style>

</style>