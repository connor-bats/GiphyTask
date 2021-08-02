<template>

    <form @submit="onSubmit" class="form-control">
        <input type="text" placeholder="Search...." class="form-search" v-model="search">
        <button type="submit" class="form-button">Submit</button>
    </form>
</template>

<script>
export default {
    name: 'Search',
    data(){
        return{
            search:''
        }
    },


    methods:{
        onSubmit(e){
            e.preventDefault()
            if(e.search === ''){
                return
            }

            const s = this.search
            this.search =''
            this.$emit('search-gif',s)



        }
    }
}
</script>

<style scoped>


.form-control{
    font-family: 'Poppins', sans-serif;
    display: inline;

    
}

.form-search{
    width: 90%;
    border-radius: 2rem;
    height: 2rem;
    
}

.form-button{
    height: 2rem;
    margin-left: 5px;
    color: #743FDF;
    border-style: solid;
    border-radius: 2rem;
    padding: 0rem 1rem;
    background: #fff;
    border-color: #743FDF;
    
    
}

form input:focus{
    color: #743FDF;
    font-size: 1rem;
    background: linear-gradient(to right bottom, rgba(255,255,255,0.7), rgba(255,255,255,0.3))
}

form button:hover{
    color: #fff;
    background: #743fdf;
}




</style>