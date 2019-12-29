<template>
	<div class="home">
		<Navbar />
		<!-- <Carousel /> -->
		
		<DealDetails />
		<!-- <v-card>
			<v-img
			src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
			height="200px"
			></v-img>
			<v-card-title>
			Top western road trips
			</v-card-title>
			<v-card-subtitle>
            1,000 miles of wonder
            </v-card-subtitle>

            <v-card-actions>
				<v-btn text>Share</v-btn>

			<v-btn color="indigo" text>Explore</v-btn>
				<v-spacer></v-spacer>
				<ClickCounter />
            </v-card-actions>

            <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

		<v-card-title>dzhrdz</v-card-title>
								<v-card-subtitle>hgfdgh</v-card-subtitle>
								<v-card-text>fdhrdhzhzd</v-card-text>
								<v-card-text class="body-2 mt-n3"><span class="font-weight-bold">hhrh</span><br>bfdhdh</v-card-text>	
		</div>
    </v-expand-transition>
		</v-card>
		<v-card>
			<v-img
			src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
			height="200px"
			></v-img>
			<v-card-title>
			Top western road trips
			</v-card-title>
			<v-card-subtitle>
            1,000 miles of wonder
            </v-card-subtitle>

            <v-card-actions>
				<v-btn text>Share</v-btn>

			<v-btn color="indigo" text>Explore</v-btn>
				<v-spacer></v-spacer>
				<ClickCounter />
            </v-card-actions>

            <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

		<v-card-title>dzhrdz</v-card-title>
								<v-card-subtitle>hgfdgh</v-card-subtitle>
								<v-card-text>fdhrdhzhzd</v-card-text>
								<v-card-text class="body-2 mt-n3"><span class="font-weight-bold">hhrh</span><br>bfdhdh</v-card-text>	
		</div>
    </v-expand-transition>
		</v-card> -->

		<!-- <GetStartedBtn /> -->
		

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
		<!-- </v-container> -->
	</div>
</template>


<script>
import DealDetails from '../components/DealDetails'
// import ClickCounter from '../components/ClickCounter'


export default {
name: "Deals",
components: { DealDetails },

    
};
</script>