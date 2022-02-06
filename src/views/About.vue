<template>
 <form  >
  <label for="fname">Movie Name:</label><br>
  <input type="text" id="fname" name="fname"  v-model="bname"><br>
  <label for="lname">Movie Description:</label><br>
  <input type="text" id="lname" name="lname" v-model="description"><br>
  <label for="lname">Movie Director:</label><br>
  <input type="text" id="lname" name="lname" v-model="director"><br><br>
  <input type="submit" value="Submit" v-on:click="addmovie">
</form> 


</template>
<script>
export default {

  data(){
    return{
  bname: "",
  description:"",
  director:""
    }
  },
  methods: {
   
         async addmovie(){


           const m= {
             id: Math.floor(Math.random(100)),
             name: this.bname,
             description:this.description,
             director: this.director
           }

  alert(m)
  const res = await fetch('http://localhost:5000/movieList',{
    method: 'POST',
    headers: {
      'Content-type': 'application/json',
    
    },
      body:JSON.stringify(m)
  })
  const data = await res.json()

}
    
 
    
  },
 

}
</script>