<template>
  <main>
      <div v-for="(movie, item) in movieArray" :key="item" class="card_movie">
          <div class="card">
              <p>Titolo: {{movie.title}}</p>
              <p>Titolo in originale: {{movie.original_title}}</p>
              <p>Lingua: {{movie.original_language}}</p>
              <p>Voto: {{movie.vote_average}}</p>
          </div>
          <!-- titolo, titolo-originale, lingua, voto -->
      </div>
  </main>
</template>

<script>
export default {
    name: 'Main',
    props:['movieArray']

}
</script>

<style>

</style>