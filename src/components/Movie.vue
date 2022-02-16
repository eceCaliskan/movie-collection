<template>
<li v-for="ok in movieList" :key="ok.id" >
		<div id="cart">
	<h2>{{ movie.name }}</h2>
			<p>{{ movie.description }}</p>
			<b><p>{{ movie.director }}</p></b>
    </div>
	</li>
</template>
<script>
export default {
    
    props: {
         movie
    }
}
</script>