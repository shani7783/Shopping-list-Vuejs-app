<template>
	<div id="app" >
		<img src=".\assets\header.png">
		<h1>My Shopping List App!</h1>
		<ShoppingList/>
	</div>
</template>

<script>
import ShoppingList from './components/ShoppingList.vue'

export default {
	components: {
		ShoppingList
	}
}
</script>

<style>

*, *::before, *::after {
	box-sizing: border-box;
}

#app {
	max-width: 400px;
	margin: 0 auto;
	line-height: 1.4;
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	color: #32485F;
}

h1 {
	text-align: center;
}
</style>