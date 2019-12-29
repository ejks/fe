<template>
<v-container class="px-0">
	<v-layout row class="mx-auto">
		<v-flex xs12 sm10 md6 lg4>
  <v-card tile
	class="mb-6"
	xs12 md6 lg4
	v-for="deal in details"
	:key="deal.id"
	>		
    <v-img
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      height="200px"
    ></v-img>
	<v-layout row class="mx-3 px-1 mb-0 pb-0">
    <v-card-title class="mb-0 pb-0">
      {{deal.title}}
    </v-card-title>
</v-layout>
<v-layout row class="ml-3 mr-3 mt-0 px-1 pt-0">
    <v-card-subtitle class="font-weight-bold mt-1 pt-1">
		{{deal.time}}
    </v-card-subtitle>
    <v-spacer></v-spacer>
	<v-btn class="mt-0 pt-0" text>
        <v-icon small>mdi-map-marker</v-icon>200 m
     </v-btn>
     <v-card-text class="py-0">
			{{deal.description}}
		</v-card-text>
     </v-layout>
    <v-card-actions class="pt-0 pb-0 mb-0 mt-0">

      <v-spacer></v-spacer>

      <v-btn
		class="pt-0 pb-0 mt-n4 mb-1"
        icon
        @click.native="deal.show = !deal.show"
      >
        <v-icon>{{ deal.show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
      </v-btn>
    </v-card-actions>

    <v-expand-transition>
      <div v-show="deal.show">
		<v-layout row class="mx-3 px-1 mb-0 pb-0">
        <v-card-text class="mt-0 pt-0"><v-span class="font-weight-bold">Disclaimer</v-span><br>{{deal.disclaimer}}
        </v-card-text>
        <v-btn>
			get coupon
        </v-btn>
        <v-btn>
			share
        </v-btn>
		</v-layout>
		<v-divider class="my-5"></v-divider>
		<v-list-item>
      <v-list-item-avatar color="grey"></v-list-item-avatar>
      <v-list-item-content>
        <v-list-item-title class="headline">{{deal.restaurant}}</v-list-item-title>
      </v-list-item-content>
    </v-list-item>
    <v-layout row class="mx-5">
		<v-btn text class="pb-0 mb-n3">
		<v-span class="font-weight-bold body">{{deal.address}}</v-span>
		
		<v-icon class="ml-12" right>mdi-map</v-icon>
	</v-btn>
		<v-card-text>
			{{deal.description}}
		</v-card-text>
    </v-layout>
    <v-img
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      height="200px"
    ></v-img>
      </div>
    </v-expand-transition>
  </v-card>
</v-flex>
</v-layout>
</v-container>
</template>

<script>
export default {
  name: "DealDetails",
  mounted(){
	this.addShow()
  },
  methods: {
	addShow() {
		this.details = this.details.map(details => ({
			...details,
			show: false
		}))
	}
  },
// import ClickCounter from './ClickCounter';

// export default {
// name: "DealDetails",
// // components: { ClickCounter },
data: () => ({
      details: [
          { id: 1, src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Stickstick", title: "50% off Chicken Skewers", time: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks at our Xuhui location. Share this deal  with your friends and enjoy it together.", distance: "300 m", disclaimer: "Offer only applies to individuals who have claimed the deal through Gast. Limit of 5 skewers per person. Offer is on between 20.00 - 22.00.", address: "Xinhua Rd, No 245, Xuhui"},
		{ id: 2, src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Bones", title: "Buy one get one Rib racks", time: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks..", distance: "200 m"},
		{ id: 3, src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Cocola", title: "75% off all cakes", time: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks..", distance: "100 m"}
        ]
    })
}
</script>
