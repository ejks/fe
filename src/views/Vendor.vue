<template>
	<div class="vendor">
		<v-img height="300px" src="../assets/cross.jpg">
		</v-img>
		<v-col align="center">
		<v-avatar class="mt-n12" size="170" color="gray">
				<img
        src="../assets/avatar.png"
        alt="John"
      >
			</v-avatar>
			<v-btn depressed dark class="button mb-6" width="80%">add new deal
			</v-btn>
			<p class="headline font-weight-medium mb-0">BoomBoom</p>
			<p class="subtitle-1">Café</p>
			<v-layout row class="justify-end mx-5">
				<v-btn text class="mt-n12 pt-0">
					<v-icon right>mdi-pencil</v-icon>
				</v-btn>
		</v-layout>
		</v-col>
		<v-layout row class="mx-9">
			<p class="title font-weight-bold">Description</p>
			<p class="body1 font-weight-regular">From an upscale cocktail lounge to a burger and fries dive, there are many different personalities your new restaurant or bar can assume. Defining your mission statement is an important way that you can attract the right customers and reinforce your goals, which can set you up for long-term success.</p>
			<p class="title font-weight-bold mb-0">Saved Deals</p>
			
		</v-layout>
	</div>
</template>
<script>
export default {

}
</script>
<style>
	.vendor {
		background-color: #FFF;
	}
	.button {
		background-color: #DFA937!important; 
		border-radius: 5px;
	}
</style>