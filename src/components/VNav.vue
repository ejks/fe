<template>
	<nav>
		<v-layout class="justify-center">
			<v-app-bar app text class="hidden-sm-and-down">
				<v-flex class="justify-space-around">
					<v-btn text color="grey darken-1" to="/deals">
						<span>Browse Coupons</span>
						<v-icon right>mdi-sale</v-icon>
					</v-btn>
				</v-flex>
				<!-- <v-spacer></v-spacer> -->
				<v-flex>
					<v-btn text color="grey darken-1">
						<v-icon>mdi-sprout-outline</v-icon>
					</v-btn>
				</v-flex>
				<!-- <v-spacer></v-spacer> -->
				<v-flex>
					<v-btn text color="grey darken-1">
						<span>Profile</span>
						<v-icon right>mdi-account</v-icon>
					</v-btn>
				</v-flex>
			</v-app-bar>
		</v-layout>

		<v-bottom-navigation
			class="hidden-md-and-up"
			grow
			fixed
			color="#DFA937"
			width
			height
		>
			<v-btn to="/vendor">
				<span>vendor</span>
				<v-icon>mdi-sale</v-icon>
			</v-btn>
			<v-btn to="/vendors">
				<span>Gäst</span>
				<v-icon>mdi-sprout-outline</v-icon>
			</v-btn>
			<v-btn to="/profile">
				<span>Profile</span>
				<v-icon>mdi-account</v-icon>
			</v-btn>
		</v-bottom-navigation>
	</nav>
</template>

<script>
	export default {};
</script>
<style>
	.v-bottom-navigation {
		bottom: 0;
		left: 0;
		right: 0;
		/*position: absolute;*/
	}
	.v-btn {
		margin: 0.5rem;
	}
	.v-toolbar {
		top: 0;
	}
</style>
