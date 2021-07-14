<template>
    <div class="star">
        <i class="fas fa-star" :class="star > 1 ? 'red' : ''"></i>
        <i class="fas fa-star" :class="star >= 4 ? 'red' : ''"></i>
        <i class="fas fa-star" :class="star >= 6 ? 'red' : ''"></i>
        <i class="fas fa-star" :class="star >= 8 ? 'red' : ''"></i>
        <i class="fas fa-star" :class="star > 9 ? 'red' : ''"></i>
    </div>
</template>

<script>
export default {
    name: 'Star',
    props:['star']

}
</script>

<style lang="scss" scoped>
    .red{
    color: red;
    }
</style>