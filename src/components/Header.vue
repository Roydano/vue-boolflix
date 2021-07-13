<template>
  <div class="search_bar">
      <h1>Boolflix</h1>
      <input type="text" v-model.trim="textSearch" @keyup.enter="$emit('search', textSearch)">
      <button @click.prevent="$emit('search', textSearch)">Cerca</button>
  </div>
</template>

<script>
export default {
    name: 'Header',

    data(){
        return{
            textSearch: ''
        }
    },
}
</script>

<style>

</style>