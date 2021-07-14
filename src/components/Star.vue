<template>
    <!-- cicliamo con un for le stelle rosse e bianche -->
    <div class="star">
        <i v-for="n in starRange" :key="n" class="fas fa-star red"></i>
        <i v-for="n in starRangeWhite" :key="n" class="fas fa-star"></i>
    </div>
</template>

<script>
export default {
    name: 'Star',
    props:['star'],

    // creiamo nel computed due funzioni che vadano a identificare il voto che abbiamo passato tramite la props e nel primo caso arrotonda per eccesso il voto e lo divide per due ritornando le stelle rosse, mentre nel secondo sottrae il numero totale di stelle assegnabili sottraendo quelle date in precedenza restituendole bianche
    computed:{
        starRange(){
            if( !this.star ) return []
            return Array( parseInt( this.star / 2 ) )
        },
        starRangeWhite(){
            if( !this.star ) return Array( 5 )
            return Array( 5 - parseInt( this.star / 2 ) )
        }
    }

}
</script>

<style lang="scss" scoped>
    .red{
    color: red;
    }
</style>