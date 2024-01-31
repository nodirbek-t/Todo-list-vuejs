<template >
 <li class="List-group-item d-flex justify-content-between"
 :class="[{like:movie.like},{favourite:movie.favourite}]"
 >
    <span class="List-group-item-label" @click="$emit('onToggle',{id:movie.id, prop:'like'})">{{ movie.name }}</span>
    <input type="number" class="List-group-item-input" :value="movie.viewers" >
    <div class="d-flex justify-content-center align-items-center">
        <button type="button" class="btn-cookie btn-sm" @click="$emit('onToggle',{id:movie.id,  prop:'favourite'})">
            <i class="fas fa-cookie"></i>
        </button>
        <button type="button" class="btn-trash btn-sm" @click="$emit('onRemove',movie.id)">
            <i class="fas fa-trash"></i>
            
        </button>
         <i class="fas fa-star" ></i>
       
    </div>
</li> 

</template>
<script>
export default {
   props:{
    movie: {
        type: Object,
        required: true,
    }
   },
   methods:{
    onLike() {
        this.$emit('onLike',this.movie.id) 
    }
   }
}
</script>
<style scoped>
.List-group-item {
    padding: 15px 20px;
    border-bottom: 1px solid red;
}
.List-group-item:last-child {
    border-bottom:none;
}
.List-group-item span {
    line-height:35px;
    font-size: 20px;
    cursor:pointer;
    width:550px;
}
.List-group-item input {
    line-height:35px;
    font-size: 20px;
    text-align: center;
    border: 0;
    outline:0;
}

.List-group-item button {
    width:35px;
    height:35px;
    margin:3px;
    font-size: 17px;
    border:none;
    cursor:pointer;
}
.List-group-item .btn-cookie {
    color:#e09f3e;
}
    
.List-group-item .btn-trash {
    color:#e5383b;
}
.List-group-item.fa-star{
   width:35px;
   height:35px;
   text-align: center;
   line-height: 35px;
   font-size: 16px;
   color:#ffe900;
   transition:0.3s all ;
   transform:translateX(30px) ;
   opacity: 0;
}

.List-group-item.like.fa-star{
    opacity:0;
    transform:translateX(10px);
}

.List-group-item.favourite .List-group-item-label{
    color:#e09f3e;
}
.List-group-item.favourite .List-group-item-input {
    color:#e09f3e; 
}


    
  
    
</style>