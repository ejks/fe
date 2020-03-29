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
			<v-layout row class="justify-end mx-5">
				<v-btn text class="mt-n12 pt-0">
					<v-icon right>mdi-logout</v-icon>
				</v-btn>
			</v-layout>
			<v-btn depressed dark class="button mb-6" width="80%" @click="dialog = true">add new deal
			</v-btn>
			<p class="headline font-weight-medium mb-0">BoomBoom</p>
			<p class="subtitle-1">Café</p>
			<v-layout row class="justify-end mx-5">
				<v-btn text class="mt-n12 pt-0">
					<v-icon right>mdi-pencil</v-icon>
				</v-btn>
				<v-dialog
      v-model="dialog"
      max-width="290">
      <!-- <v-card> -->
			
		<v-card>
			<v-layout row class="mx-auto">
				<v-card-title class="headline">Add new Deal</v-card-title>
				<v-spacer></v-spacer>
				<v-btn icon @click="dialog = false">
				<v-icon>mdi-close</v-icon>
          </v-btn>
        </v-layout>
				<v-form
    ref="form"
    v-model="valid"
    lazy-validation
    class="mx-5"
  >

    <v-text-field
      v-model="title"
      label="Title"
      required
      color="#DFA937"
    ></v-text-field>
    <v-textarea
        v-model="description"
        color="#DFA937"
        >
        <template v-slot:label>
            <div>
              Description 
            </div>
        </template>
    </v-textarea>
	<v-checkbox
	v-model="allday"
	color="green"
	>
	<template  v-slot:label>
		<div>
			All day deal
		</div>
	</template>
	</v-checkbox>
	<v-text-field
      v-model="start"
      label="Start-time"
      required
      color="#DFA937"
    ></v-text-field>
    <v-text-field
      v-model="end"
      label="End-time"
      required
      color="#DFA937"
    ></v-text-field>
    <v-file-input
		label="Deal Photo"
		prepend-icon="mdi-camera"
	></v-file-input>
	
		
  </v-form>
<!-- </v-layout> -->
<!-- </v-card> -->

        <v-card-actions class="d-flex justify-space-around pb-3">

          <v-btn
            width="50%" dark color="#DFA937" tile class="buttons" depressed @click="dialog = false">
            save & post
          </v-btn>
          <v-btn
            width="40%" dark color="#DFA937" tile class="buttonst" depressed @click="dialog = false">
            save
          </v-btn>
           </v-card-actions>
      </v-card>
    </v-dialog>
		</v-layout>
		</v-col>
		<v-layout row class="mx-9">
			<p class="title font-weight-bold">Description</p>
			<p class="body1 font-weight-regular">From an upscale cocktail lounge to a burger and fries dive, there are many different personalities your new restaurant or bar can assume. Defining your mission statement is an important way that you can attract the right customers and reinforce your goals, which can set you up for long-term success.</p>
			<p class="title font-weight-bold">Saved Deals</p>
			<VendorCard />
			
		</v-layout>
	</div>
</template>
<script>
import axios from 'axios'
import VendorCard from '../components/VendorCard.vue'
export default {
	name: "Vendor",
	components: { VendorCard },
	created() {
		axios.get('http://localhost:3000/api/v1/vendors.json') 
		.then(response => {
			this.details = response.data.cards
			this.details = this.details.map(details => ({
        ...details,
        dialog: false,
		dialog2: false,
		}))
		})
		.catch(e => {
			this.error.push(e)
		})
	},
	data() {
		return {
		}
    },
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
	.buttons {
	border-radius: 5px;
}
.buttonst {
	border-radius: 5px;
	background-color: rgba(223, 169, 55, 20%)!important;
	color: #DFA937!important;
}
</style>