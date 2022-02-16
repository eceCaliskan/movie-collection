<template>
<div id="ok">
   <Header />
    <p><b>You have {{size}} movies in your collection</b></p>
</div>
 <li v-for="movie in movieList" :key="movie.id">
   <div id="cart">
       <h2>{{movie.name}}</h2>
       <p>{{movie.description}}</p>
       <b><p>{{movie.director}}</p></b>
    <Button @remove='remove(movie.id)'/>
       <hr style="width:80%;text-align:center;">
   </div>
 </li>
</template>

<script>
import Button from '/src/components/Button'
import Header from '/src/components/Header'

import { watch } from '@vue/runtime-core';
export default {
  
  name: 'App',
  components: {
    Button,
    Header
  },
  data() {
    return{
     
    movieList: []
    
  }
},
methods: {
       async remove(id){
         alert("ok");
         const res =  fetch("http://localhost:5000/movieList/"+id,{
         method: 'DELETE',
     })
 //refreshing the page
   this.$router.go()
 
  
},

async fetchTasks() {
     const res = await fetch('http://localhost:5000/movieList')
     const data = await res.json()

     return data
     
},

},
 async created()
{
     
     this.movieList =  await this.fetchTasks()
     if(this.movieList.length===0){
       alert("Your movie list is empty")
     }
},

computed: {
  size(){
    return this.movieList.length;
  }

}


}
</script>

<style>
body{
  background-color: rgb(230, 230, 230);

}

li{
  list-style: none;
}

h2{
  color: rgb(110, 161, 219);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 8vh;
  margin-left: 100px;
  margin-right: 100px;
  
}

#cart{
  background-color: aliceblue;
  margin-right: 100px;
   margin-left: 100px;
     margin-bottom: 50px;
}

div{
  padding-top: 5px;
  padding-bottom: 5px;
  background-color: #fff;
}

p{
  margin-left: 100px;
margin-right: 100px;
}

/* CSS */

</style>







