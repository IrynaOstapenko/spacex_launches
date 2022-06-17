<template>
	<Navigation />
	<div class="hero">
		
	</div>
</template>

<script>
	import Navigation from '../components/Navigation.vue';

	export default {
		components: {
			Navigation
		},
		data() {
			
		}
	}
</script>

<style scoped>
	.hero {
		width: 100%;
		height: 100%;
		position: relative;
		background-image: linear-gradient(rgba(0, 0, 0, 0.2),rgba(0, 0, 0, 0.2)), url('/images/space-stars.jpg');
		background-position: center;
		background-repeat: no-repeat;
		background-size: cover;
		overflow-x: hidden;
	}


</style>

