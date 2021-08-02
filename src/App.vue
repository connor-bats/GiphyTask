<template>
  <Header/>
  <Search @search-gif="searchGif"/>

  <Gif :gifArr="gifArr" v-if="gifArr" />

  
</template>

<script>
import Header from './components/Header.vue';
import Gif from './components/Gif.vue';
import Search from './components/Search.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Gif,
    Search
    
  },
  data(){

    return {
      
      gifArr:[]      
    }

  },

  methods:{
    getGifs(query){

      if(query === ''){
        console.log('This is running')
        axios.get('https://api.giphy.com/v1/gifs/trending?api_key=dc6zaTOxFJmzC&limit=1000')
          .then(res =>{
            console.log(res.data)
            this.gifArr = [...res.data.data]
            console.log(this.gifArr)
          })

          .catch(err =>{
            console.log(err)
          })



      }

      else{
        console.log('This is not running')
        console.log(query)
        axios.get(`https://api.giphy.com/v1/gifs/search?api_key=dc6zaTOxFJmzC&q=${query}&limit=1000`)
          .then(res =>{
            console.log(res.data)
            this.gifArr = [...res.data.data]
            console.log(this.gifArr)
          })

          .catch(err =>{
            console.log(err)
          })




      }
      

    },

    searchGif(query){
      this.getGifs(query)
    }
  },

  created(){
    this.getGifs('')

  }

  
}

 
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;1,200;1,300&display=swap');
#app {
  margin-left: 1rem;
  

  font-family: 'Poppins',sans-serif ;

  
}
</style>
