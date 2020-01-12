<template>
	<div class="home mb-12 pb-5">
		<Navbar />
		<v-img height="200px" src="../assets/cross.jpg">
		</v-img>
		<v-layout row class="mx-9 my-8">
			<p class="font-weight-medium text-center">Find deals on food that needs to be consumed today!</p>
			<v-btn dark block color="#DFA937" tile class="buttons" depressed>
				user login to find deals
				<v-icon right>mdi-wechat</v-icon>
			</v-btn>
			<v-btn tile class="buttonst" block depressed to="/vendors">
				vendors click here to start
				<v-icon right>mdi-store</v-icon>
			</v-btn>
			<v-list>
				<p class="font-weight-medium">Our partners are not allowed to sell:</p>
      <v-list-item
        v-for="item1 in items1"
        :key="item1.title"
      >
        <v-list-item-icon>
          <v-icon v-if="item1.icon" color="red">mdi-cancel</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title v-text="item1.title" class="font-weight-medium"></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
	<v-list>
		<p class="font-weight-medium">The reasons why food end up on our site could be one of the following reasons:</p>
      <v-list-item
        v-for="item in items"
        :key="item.title"
      >
        <v-list-item-icon>
          <v-icon v-if="item.icon" color="orange">mdi-carrot</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title v-text="item.title" class="font-weight-medium"></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
		</v-layout>
	</div>
</template>
<script>
import Navbar from '../components/Navbar'

export default {
	name: "Home",
	components: { Navbar },
	data () {
		return {
		items: [
		{ icon: true, title: "Overproduction" },
		{ icon: true, title: "Short time until best before date" },
		{ icon: true, title: "Season specific food" },
		{ icon: true, title: "Packaging deformation" },
		{ icon: true, title: "Production mistakes"}
		],
		items1: [
		{ icon: true, title: "Spoiled food" },
		{ icon: true, title: "Food waste" }
		],
		dialog: false
	}
	},
}
</script>

<style scoped>
.home {
	background-color: #FFF;
}
.buttons {
	border-radius: 5px;
}
.buttonst {
	border-radius: 5px;
	background-color: rgba(223, 169, 55, 20%)!important;
	color: #DFA937!important;
}
</style>