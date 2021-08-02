<template>

    <div class="container">
        <div :key="gif.id" v-for="gif in gifArr" >

        
            <div class="card">
                <img :src="gif.images.original.url" alt="Gif image alternate" class="flex-images">


            </div>
            

        </div>   

    </div>
    
</template>


<script>
export default {
    name: 'Gif',
    props:{
        gifArr: Array
    }
    
}
</script>


<style scoped>
.container{
    margin-top: 2rem;
    display: grid;
    grid-template-columns: 33% 33% 33%;
    grid-column-gap: 10px;
    grid-row-gap: 2rem;
    
    
    
    
}

.card{
    width:100%;

    height: 70vh;
    
}



.card img{
    object-fit: cover;
    margin-left: auto;
    margin-right: auto;
    width: 80%;
    height: 60%;
    

}

.card img:hover{
    opacity: 0.7;
}







</style>