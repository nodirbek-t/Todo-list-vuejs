<template >
    <ul class="movie-list list-group">
        <MovieListitem v-for="movie in movies" 
        :movie="movie" 
        :key="movie.id"
        @onToggle="$emit('onToggle',$event)"
        @onRemove="$emit('onRemove',$event)"

        
       
        />
        
    </ul>
</template>
<script>
 import MovieListitem from '@/component/Movie-list-item/MovieListitem.vue'
export default {
    components:{MovieListitem},
    props:{
        movies:{
            type:Array,
            required:true,
        }
    }
}
</script>
<style scoped>
   .movie-list{
    font-size: large;
    font-family: sans-serif;
    cursor: pointer;
    padding:1.5rem;
    border-radius: 4px;
    box-shadow: 20px 20px 20px rgba(0, 0, 0, 10);
   }
</style>