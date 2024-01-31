<template>
    
    <div class="appinfo">
        <p class="fs-3 text-uppercase">Barcha kinolar soni:{{ allMoviesCount }}</p>
        <p class="fs-4 text-uppercase">Ko'rilgan kinolar soni :{{ favouriteMoviesCount }}</p>
    </div>
</template>

<script>
    export default {
        props:{
            allMoviesCount:{
                type:Number,
                required:true,

            },
            favouriteMoviesCount:{
                type:Number,
                required:true,
            },
        }

    }
</script>
<style scoped>
 .appinfo{
    padding:1.5rem;
    border-radius: 4px;
    box-shadow: 20px 20px 20px rgba(0, 0, 0, 10);
 } 
</style>