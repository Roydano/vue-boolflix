<template>
  <main>
      <h2>Movie</h2>
      <div v-for="movie in movieArray" :key="movie.id" class="card_movie">
          <div class="card">
              <p>Titolo: {{movie.title}}</p>
              <p>Titolo in originale: {{movie.original_title}}</p>
              <p>Lingua: {{movie.original_language}}</p>
              <p>Voto: {{movie.vote_average}}</p>
          </div>
          <!-- titolo, titolo-originale, lingua, voto -->
      </div>
    <h2>Tv Series</h2>
      <div v-for="series in seriesArray" :key="series.id" class="card-serie">
          <div class="card">
              <p>Titolo: {{series.name}}</p>
              <p>Titolo in originale: {{series.original_name}}</p>
              <p>Lingua: {{series.original_language}}</p>
              <p>Voto: {{series.vote_average}}</p>
          </div>
      </div>
  </main>
</template>

<script>
export default {
    name: 'Main',
    props:['movieArray', 'seriesArray']

}
</script>

<style>

</style>