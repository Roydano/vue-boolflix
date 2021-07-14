<template>
  <div v-if="movie.poster_path != null" class="img_card">
        <img :src='imgUrl + movie.poster_path' alt="">
        
        <div class="card">
            <p>Titolo: {{movie.title == null ? movie.name : movie.title}}</p>
            <p>Titolo in originale: {{movie.original_title == null ? movie.original_name : movie.original_title}}</p>
            <p>Lingua: {{movie.original_language}} <img :src="'https://www.countryflags.io/' + changeIdLang(movie.original_language) + '/flat/64.png'" :alt='movie.original_language' class="flag"></p>
             <div>
                <p v-if="movie.overview != '' ">Descrizione: {{movie.overview}}</p>
                <p v-else>Nessuna descrizione presente</p>
            </div>
            <p>Voto: {{movie.vote_average}} <Star :star="movie.vote_average"/></p>
        </div>
        
    </div>

    <div v-else class="unknown img_card">
        <h4 class="text-center pt-3">{{movie.title == null ? movie.name : movie.title}}</h4>

        <div class="card">
            <p>Titolo: {{movie.title == null ? movie.name : movie.title}}</p>
            <p>Titolo in originale: {{movie.original_title == null ? movie.original_name : movie.original_title}}</p>
            <p>Lingua: {{movie.original_language}} <img :src="'https://www.countryflags.io/' + changeIdLang(movie.original_language) + '/flat/64.png'" :alt='movie.original_language' class="flag"></p>
            <div>
                <p v-if="movie.overview != '' ">Descrizione: {{movie.overview}}</p>
                <p v-else>Nessuna descrizione presente</p>
            </div>
            
            <p>Voto: {{movie.vote_average}} <Star :star="movie.vote_average"/></p>

        </div>

    </div>
</template>

<script>
import Star from '@/components/Star.vue';


export default {
    name: 'Card',
    props: ['movie'],

    components:{
        Star
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
        box-shadow: 1px 1px 1px 1px black;
        
        &:hover .card{
            display: block;
        }
        

        img{
            height: 100%;
            width: 100%;
        }

        .card{
            display: none;
            position: absolute;
            top: 0;
            left: 0;
            height: 450px;
            width: 300px;
            padding: 10px;
            background-color: yellow;

            .flag{
            width: 10%;
            }
        }
    }

    .unknown{
        height: 450px;
        width: 300px;
        background-image: url(http://nmdinteriors.com/images/no_image.png);
        background-size: contain;
        background-repeat: no-repeat;
        background-position: center;
        background-color: rgb(59, 59, 59);
    }
    
    
</style>