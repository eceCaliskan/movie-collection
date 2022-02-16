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
