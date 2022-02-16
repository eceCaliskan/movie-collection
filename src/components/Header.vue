<template>
	<h1>{{ title }}</h1>
</template>

<script>
import Button from "/src/components/Button";

export default {
	
	data() {
		return {
			title: "Movie Collection"
		};
	}
}
</script>

<style scoped>
h1{
	font-size: 50px;
	font-weight: normal;
	font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}
</style>