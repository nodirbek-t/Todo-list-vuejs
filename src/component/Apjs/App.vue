<template>
  <div class="app font-monospace">
    <div class="container">
      <Appinfo :allMoviesCount="movies.length"
        :favouriteMoviesCount="movies.filter(c=>c.favourite).length"/>
      <div class="search-panel">
        <Searchpanel :updateTermHandler="updateTermHandler"/>
        <appFilter   :updateFilterHandler="updateFilterHandler" :filterName="filter"/>
      </div>
      <moveList :movies="onFilterHandler(onSearchHandler(movies,term),filter)" 
      @onToggle="onToggleHandler"
      @onRemove="onRemoveHandler"
      
      />
      <MovieAddForm  @createMovie="createMovie"/>
    </div>
  </div>
  
  </template>

<script>
  import Appinfo from '@/component/Apinfo/Appinfo.vue'
  import Searchpanel from '@/component/search-panel/Searchpanel.vue'
  import appFilter from '@/component/app-filter/appFilter.vue'
  import moveList from '@/component/Movie-list/moveList.vue'
  import MovieAddForm from'@/component/Movie-add-form/MovieAddForm.vue'
 
  export default {
    components:{
       Appinfo, Searchpanel,appFilter,moveList,MovieAddForm,
    },
    data() {
        return{
            movies:[
                {
                    name:'omar',
                    viewers:"800",
                    favourite:true,
                    like:false,
                    id:1,
                },
                {
                    name:'farsaj',
                    viewers:"500",
                    favourite:false,
                    like:true,
                    id:2,
                    
                },
                {
                    name:'empire of osman',
                    viewers:"600",
                    favourite:true,
                    like:false,
                    id:3,
                }
            ],
           term:'',
           filter:'all',
        }
    },
    methods:{
      createMovie(item){
        this.movies.push(item)
       
      },
      onToggleHandler({id,prop}){
        console.log(prop)
        this.movies =this.movies.map(item=>{
          if(item.id==id){
            return {...item, [prop]:!item[prop] }
          }
          return item
        })
        
      },
      onRemoveHandler(id){
        this.movies=this.movies.filter(c=>c.id!=id)
      },
      onSearchHandler(arr,term){
        if(term.length==0){
          return arr
        }
        return arr.filter(c=>c.name.toLowerCase().indexOf(term)>-1)
      },
      onFilterHandler(arr,filter){
        switch(filter){
          case 'popular':
            return arr.filter(c=>c.like)
          case 'mostViewers':
            return arr.filter(c=>c.viewers>500)
          default:
            return arr
        }
      },
      updateTermHandler(term){
        this.term=term
      },
      updateFilterHandler(filter){
        this.filter=filter
      }

    }

  }
</script>

<style>
  .app {
    height:100vh;
    color: black;
  }
  .container{
    width:1000px;
    min-height: 700px;
    background-color: #fff;
    margin:0 auto ;
    padding: 5rem 0;
  }
 .search-panel {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color:#fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 10);
 }

</style>
