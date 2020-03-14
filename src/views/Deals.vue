<template>
	<div class="home">
		<Navbar />
		<Carousel />
		<DealDetails />
		<v-footer color="white" padless class="mb-12">
			<v-row justify="center" no-gutters>
				<p class="caption ma-2 pt-3 text-center">
					Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur,
					rerum! Modi illo deserunt excepturi similique ea magni.
				</p>
				<v-col class="#FFF py-4 text-center gray--text" cols="12">
					{{ new Date().getFullYear() }} — <strong>Gäst</strong>
				</v-col>
			</v-row>
		</v-footer>
	</div>
</template>

<script>
	import DealDetails from '../components/DealDetails';
	import Carousel from '../components/Carousel';
	import Navbar from '../components/Navbar';

	export default {
		name: 'Deals',
		components: { DealDetails, Carousel, Navbar }
	};
</script>
