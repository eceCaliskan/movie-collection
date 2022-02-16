<template>
    <li>
       <h2>{{movie.name}}</h2>
       <p>{{movie.description}}</p>
       <b><p>{{movie.director}}</p></b>
     <Button v-on:remove="$emit('remove')"/>
    </li>
</template>


<script>
import Button from "/src/components/Button";

export default {
    components: {
		Button
	},
    props: {
        movie: Object
    }
    
}
</script>
<style>
body {
	background-color: rgb(230, 230, 230);
}

li {
	list-style: none;
}

h2 {
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

#cart {
	background-color: aliceblue;
	margin-right: 100px;
	margin-left: 100px;
	margin-bottom: 50px;
}

div {
	padding-top: 5px;
	padding-bottom: 5px;
	background-color: #fff;
}

p {
	margin-left: 100px;
	margin-right: 100px;
}

/* CSS */
</style>
