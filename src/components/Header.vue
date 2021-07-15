<template>
    <header class="text-center">
        <h1>Boolflix</h1>
        <div class="search_bar pb-4">
            <input class="mx-3" type="text" placeholder="Inserisci il titolo di un Film o di una Serie TV..." v-model.trim="textSearch" @keyup.enter="$emit('search', textSearch)">
            <button @click.prevent="$emit('search', textSearch)">Cerca</button>
            <select class="ms-5 text-center" name="genre" id="genre">
                <option value="">Seleziona un genere</option>
                <option v-for="genre in genreArray" :key="genre.id" value="">{{genre.name}}</option>
            </select>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    props:['genreArray'],

    data(){
        return{
            textSearch: ''
        }
    },
}
</script>

<style lang="scss" scoped>

    header{
        background-color: black;

        
        h1{
            color: red;
            font-size: 50px;
            text-transform: uppercase;
        }

        input{
            background-color: rgb(26, 25, 25);
            color: rgb(143, 142, 142);
            padding: 5px 20px;
            border: none;
            width: 35%;
            &:focus-visible{
                outline: 1px solid red;
            }
            
        }

        button{
            padding: 5px 15px;
            border-radius: 20px;
            border-color: red;
            background-color: rgb(26, 25, 25);
            color: rgb(143, 142, 142);
            &:hover{
                color: white;
                background-color: red;
            }

        }

        select{
            background-color: black;
            color: red;
            border: none;
            border-bottom: 1px solid red;
            padding: 2px 20px;
        }
    }


</style>