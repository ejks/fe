<template>
	<div class="home">
		<Navbar />
		<Carousel />
		<!-- <GetStartedBtn /> -->
		<v-container class="px-0">
			<v-card tile class="px-0 mb-5" v-for="deal in details"  
			:key="deal.restaurant">

			<v-img
			src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
			height="200px"
			></v-img>

    <v-card-title>
      {{deal.restaurant}} - {{deal.title}}
    </v-card-title>

    <v-card-subtitle>
		{{deal.time}}
    </v-card-subtitle>

    <v-card-actions>
					<v-dialog v-model="dialog" fullscreen hide-overlay transition="dialog-bottom-transition">
						<template v-slot:activator="{ on }">
						<v-btn color="success" dark v-on="on" class="ml-4">See Details</v-btn>
						</template>
						<v-card>
							<v-img
							height="350"
							src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
							>
								<v-btn icon dark @click="dialog = false">
									<v-icon>mdi-close</v-icon>
								</v-btn>
							</v-img>
							<v-col
							cols="12">
								<v-card-title>{{deal.title}}</v-card-title>
								<v-card-subtitle>{{deal.time}}</v-card-subtitle>
								<v-card-text>{{deal.description}}</v-card-text>
								<v-card-text class="body-2 mt-n3"><span class="font-weight-bold">Disclaimer</span><br>{{deal.disclaimer}}</v-card-text>	
							</v-col>
							<v-layout cols="12" class="mx-10 justify-space-around">
										<v-btn dark width="50%" @click.stop="dialog2 = true">Get Coupon</v-btn>
										<v-dialog
										v-model="dialog2"
										max-width="290"
										>
										<v-card>
											<v-card-title class="headline">Success!</v-card-title>
											<v-card-text>You have successfully claimed this deal.</v-card-text>
											<v-card-actions>
												<v-spacer></v-spacer>
												<v-btn text color="green darken-1" @click="dialog2 = !dialog2">See in account</v-btn>
											</v-card-actions>
										</v-card>
											<!-- <v-card>
												<v-card-title class="headline">Success!</v-card-title>

												<v-card-text>
												You have successfully created this deal!
												</v-card-text>
												<v-card-text class="body-2 mt-n3"><span class="font-weight-bold">Disclaimer Reminder</span><br>{{deal.disclaimer}}</v-card-text>	

												<v-card-actions>
												<v-spacer></v-spacer>

												<v-btn
												color="green darken-1"
												text
												@click="dialog2 = false"
												>
													See in profile
												</v-btn>
											</v-card-actions> -->
										<!-- </v-card> -->
										</v-dialog>
										<v-btn outlined width="50%">Share</v-btn>
									</v-layout>
									<br>
								<v-divider class="mx-4"></v-divider>
								<br>
								<v-layout cols="12" class="mx-10 justify-space-around">
								<v-list-item>
									<v-list-item-avatar size="62" color="grey">
										<img
        src="https://cdn.vuetifyjs.com/images/john.jpg"
        alt="John"
      >
									</v-list-item-avatar>
									<v-list-item-content>
										<v-list-item-title class="title">{{deal.restaurant}}</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
							</v-layout>
							<v-layout cols="12">
								<v-list-item class="mt-n3">
									<v-btn block text x-small class="caption font-weight-bold justify-start pa-0 mb-0 mb-n4">{{deal.address}}<v-spacer></v-spacer>
									<v-icon class="pr-12">mdi-map</v-icon>
									</v-btn>
								</v-list-item>
							</v-layout>
							<v-layout cols="12">
								<v-list-item>
									<v-btn block x-small text class="caption font-weight-bold justify-start pa-0 mt-n1">+86 136 8888 8888<v-spacer></v-spacer>
									<v-icon class="pr-12">mdi-phone</v-icon>
									</v-btn>
								</v-list-item>
							</v-layout>
							<v-col cols="12" class="mt-0 pt-0">
								<v-card-text class="pt-0 mt-0">{{deal.description}}</v-card-text>
							</v-col>
							<v-img
							height="350"
							src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
							></v-img>
						</v-card>
					</v-dialog>
					<v-spacer></v-spacer>
					<v-card-text class="caption text-end mr-4"><span><v-icon>mdi-map-marker</v-icon></span>{{deal.distance}}</v-card-text>
				</v-card-actions>

			</v-card>
			<v-footer
			color="white"
			padless
			class="mb-11"
			>
			<v-row
			justify="center"
			no-gutters
			>
			<p class="caption ma-2 pt-3 text-center">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur, rerum! Modi illo deserunt excepturi similique ea magni.</p>
				<!-- <v-btn
				v-for="link in links"
				:key="link"
				color="gray"
				text
				rounded
				class="my-2"
				>
					{{ link }}
				</v-btn> -->
				<v-col
					class="teal lighten-2 py-4 text-center gray--text"
				cols="12"
				>
			{{ new Date().getFullYear() }} — <strong>Gäst</strong>
				</v-col>
			</v-row>
			</v-footer>
		</v-container>
	</div>
</template>

<script>
// import DealDetails from '@/components/DealDetails'

export default {
	// components: { DealDetails },
	data: () => ({
		dialog: false,
		dialog2: false,
		details: [
			{ src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Stickstick", title: "50% off Chicken Skewers", time: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks at our Xuhui location. Share this deal  with your friends and enjoy it together.", distance: "300 m", disclaimer: "Offer only applies to individuals who have claimed the deal through Gast. Limit of 5 skewers per person. Offer is on between 20.00 - 22.00.", address: "Xinhua Rd, No 245, Xuhui" },
			{ src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Bones", title: "Buy one get one Rib racks", time: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks..", distance: "200 m" },
			{ src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Cocola", title: "75% off all cakes", time: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks..", distance: "100 m" }
		],
		links: [
        'Home',
        'About Us',
        'Team',
        'Services',
        'Blog',
        'Contact Us',
        ],
   //
 
      
      
  })
	

}
</script>
<style>


</style>