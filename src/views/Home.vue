<template>
<div id="ok">
    <h1><i>Movie Collection</i></h1>
</div>
 <li v-for="movie in movieList" :key="movie.id">
   <!--img  v-if="movie.id==1" src='@/assets/midnight.jpg' >
 <img  v-if="movie.id==2" src='@/assets/inception.jpg' -->

<h4>{{movie.name}}</h4>
<p>{{movie.description}}</p>
<p>{{movie.director}}</p>

<button class="button-81" v-on:click="remove(movie.id)">Remove</button>
 <hr style="width:80%;text-align:center;">
 </li>
<About @addmovie="addmovie"/>
<!--button class="button-81" v-on:click="index -=1">Back</button>

<button class="button-81" v-on:click="index +=1">Next</button-->
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
 }.this.fetchTasks())
   
 
  
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

}
</script>

<style>
body{
  background-color: rgb(230, 230, 230);

}

li{
  list-style: none;
}

h4{
  color: green;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 8vh;
  margin-left: 100px;
  margin-right: 100px;
  
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







