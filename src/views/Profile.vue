<template>
	<div class="profile">
		<Navbar />
		<v-img height="200px" src="../assets/cross.jpg">
		</v-img>
		<v-layout column class="mx-5 my-5">
			<v-list v-for="user in users" :key="user.username">
			<v-list-item>
			<v-list-item-avatar size="54" color="grey">
				<img :src="user.avatar">
			</v-list-item-avatar>
			<v-list-item-content>
				<v-list-item-title class="headline">{{user.username}}</v-list-item-title>
			</v-list-item-content>
			<v-list-item-icon>
				<v-btn fab text>
          <v-icon>mdi-logout</v-icon>
      </v-btn>
        </v-list-item-icon>
		</v-list-item>
	</v-list>
	
		<h3 class="mx-4 mt-3">Today's claims</h3>
	
		<v-list row two-line v-for="(deal, index) in deals" :key="deal.title" width="90vw">
      <v-list-item >
        <v-list-item-content>
          <v-list-item-title>{{deal.title}}</v-list-item-title>
          <v-list-item-subtitle>{{deal.time}}</v-list-item-subtitle>
        </v-list-item-content>
        <v-spacer></v-spacer>
        <v-list-item-icon @click="deal.dialog = true" class="my-0">
			<v-btn fab text>
          <v-icon>mdi-delete</v-icon>
      </v-btn>
      <v-dialog
      v-model="deal.dialog"
      max-width="290">
      <v-card>
			<v-layout row class="mx-auto">
        <v-card-title class="headline">Cancel coupon?</v-card-title>
		<v-spacer></v-spacer>
        <v-btn icon @click="deal.dialog = false">
            <v-icon>mdi-close</v-icon>
          </v-btn>
        </v-layout>

        <v-card-text>
          Are you sure you want to cancel this deal?
        </v-card-text>

        <v-card-actions class="d-flex justify-center pb-3">

          <v-btn
            width="80%" dark color="#DFA937" tile class="buttons" depressed @click="remove(index)"
          >
            cancel
          </v-btn>
           </v-card-actions>
      </v-card>
    </v-dialog>
        </v-list-item-icon>
      </v-list-item>
  </v-list>
		</v-layout>
		<v-layout justify-center>
			<v-btn
            width="80%" dark color="#DFA937" class="buttons mb-12" tile depressed to="/deals"
          >
            browse deals
          </v-btn>
		</v-layout>
		<v-footer
			color="white"
			padless
			class="mb-12"
			>
			<v-row
			justify="center"
			no-gutters
			>
			<p class="caption ma-2 pt-3 text-center">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur, rerum! Modi illo deserunt excepturi similique ea magni.</p>
				<v-col
					class="#FFF py-4 text-center gray--text"
				cols="12"
				>
			{{ new Date().getFullYear() }} — <strong>Gäst</strong>
				</v-col>
			</v-row>
			</v-footer>
		
	</div>
</template>
<script>
import Navbar from '../components/Navbar'

export default {
	name: "Profile",
	components: { Navbar },
	mounted(){
	this.addDialog()
  },
	data () {
		return {
			users: [
				{ username: "Jim Halpert", avatar: "https://cdn.vuetifyjs.com/images/cards/foster.jpg" }
			],
			deals: [
				{ id: 1, src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Stickstick", title: "50% off Chicken Skewers", time: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks at our Xuhui location. Share this deal  with your friends and enjoy it together.", distance: "300 m", disclaimer: "Offer only applies to individuals who have claimed the deal through Gast. Limit of 5 skewers per person. Offer is on between 20.00 - 22.00." },
				{ id: 2, src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Stickstick", title: "Bkhfes fjsekfg", time: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks at our Xuhui location. Share this deal  with your friends and enjoy it together.", distance: "300 m", disclaimer: "Offer only applies to individuals who have claimed the deal through Gast. Limit of 5 skewers per person. Offer is on between 20.00 - 22.00." }
			] 
		}
	},
	methods: {
		remove(id) {
			// this.deals.splice(id, 1); JavaScript
			// below VueJS delete helper
			this.$delete(this.deals, id);
		},
		addDialog() {
		this.deals = this.deals.map(deals => ({
			...deals,
			dialog: false
		}))
	}

	}
}
</script>

<style scoped>
.profile {
	background-color: white;
}
.buttons {
	border-radius: 5px;
}
</style>