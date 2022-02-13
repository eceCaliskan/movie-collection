<template>
<div id="ok">
    <h1>Movie Collection</h1>
    <p><b>You have {{size}} movies in your collection</b></p>
</div>
 <li v-for="movie in movieList" :key="movie.id">
   <div id="cart">
       <h2>{{movie.name}}</h2>
       <p>{{movie.description}}</p>
       <b><p>{{movie.director}}</p></b>
       <button class="button-81" v-on:click="remove(movie.id)">Remove</button>
       <hr style="width:80%;text-align:center;">
   </div>
 </li>
</template>

<script>
import { watch } from '@vue/runtime-core';
export default {
  
  name: 'App',
  data() {
    return{
     
    movieList: []
    
  }
},
methods: {
       async remove(id){
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

  
@media screen and (max-width: 992px) {
  img {
   width: 200px;
  }
}

/* On screens that are 600px or less, set the background color to olive */
@media screen and (min-width: 600px) {
  img {
   width: 300px;
  }
}



#back{
  margin-right: 100px;
 
}
#next{
  margin-left: 100px;
}

p{
  margin-left: 100px;
margin-right: 100px;
}

button{
  background-color: #fff;
  border-color:white;
  border-radius: 10px;
  min-width: 20%;
  padding-top: 1%;
  padding-bottom:  1%;
  

}

button:hover{
  background-color:rgb(238, 80, 80);
  color: white;
}
/* CSS */

</style>







