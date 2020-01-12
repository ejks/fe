<template>
<v-container class="px-0">
  <v-card
	class="mx-auto"
	max-width="344"
	v-for="deal in details"
	:key="deal.id"
	>		
    <v-img
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      height="200px"
    ></v-img>

    <v-card-title>
      {{deal.title}}
    </v-card-title>

    <v-card-subtitle>
      {{deal.description}}
    </v-card-subtitle>

    <v-card-actions>
      <v-btn text>Share</v-btn>

      <v-btn
        color="purple"
        text
      >
        Explore
      </v-btn>

      <v-spacer></v-spacer>

      <ClickCounter />
    </v-card-actions>

    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

        <v-card-text>
          I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to escape.
        </v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
</v-container>
</template>

<script>
import ClickCounter from './ClickCounter';

export default {
name: "DealDetails",
components: { ClickCounter },
	data ()  {
		return {
		details: [
          { id: 1, src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Stickstick", title: "50% off Chicken Skewers", time: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks at our Xuhui location. Share this deal  with your friends and enjoy it together.", distance: "300 m", disclaimer: "Offer only applies to individuals who have claimed the deal through Gast. Limit of 5 skewers per person. Offer is on between 20.00 - 22.00.", address: "Xinhua Rd, No 245, Xuhui" },
		{ id: 2, src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Bones", title: "Buy one get one Rib racks", time: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks..", distance: "200 m" },
		{ id: 3, src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Cocola", title: "75% off all cakes", time: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks..", distance: "100 m" }
        ]
    }  
    }
}
</script>