<template >
    <div class="Movie-add-form">
       <h3>Yangi kino qo'shish</h3>
       <form class="add-form d-flex" @submit.prevent>
            <input type="text" class="form-control new-form-label" placeholder="Qanday kino "
            :value="name"
            @input="name= $event.target.value">
            <input type="text" class="form-control new-form-label" placeholder="Necha marotaba ko'rilgan "
            :value="viewers"
            @input="viewers= $event.target.value">
            <button class="btn btn-outline-dark" type="submit" @click="addMovie"> Qo'shish
            </button>
       </form>

    </div>
</template>
<script>
import { setTransitionHooks } from 'vue';

export default {
    data(){
        return{
            name:"",
            viewers:"",
        }
    },
    methods: {
        addMovie(){
            if(!this.name || !this.viewers)
                reurn
            
            const Movie={
                name:this.name,
                viewers:this.viewers,
                favourite:false,
                like:false,
                id:Date.now(),
            }
            this.$emit('createMovie',Movie),
            this.name=""
            this.viewers=""
        }
    }
    
}
</script>
<style scoped>
    .new-form-label{
        font-family: sans-serif;
        color:red;

    }
    .Movie-add-form{
        margin-top: 2rem;
        padding: 1.5rem;
        background-color:#fcfaf5;
        border-radius: 4px;
        box-shadow: 15px 15px 15px rgba(0, 0, 0, 10);
    }
   
</style>