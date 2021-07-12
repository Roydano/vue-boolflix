<template>
  <main>
      <div v-for="(movie, item) in movieArray" :key="item" class="card_movie">
          {{movie.title}}
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