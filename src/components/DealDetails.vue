<template>
	<v-container class="px-0">
		<v-layout row class="mx-auto">
			<v-flex xs12 sm10 md6 lg4>
				<v-card
					tile
					class="mb-6"
					xs12
					md6
					lg4
					v-for="deal in details"
					:key="deal.id"
				>
					<v-img src="../assets/cross.jpg" height="200px"></v-img>
					<v-layout row class="mx-3 px-1 mb-0 pb-0">
						<v-card-title class="mb-0 pb-0">
							{{ deal.description }}
						</v-card-title>
					</v-layout>
					<v-layout row class="ml-3 mr-3 mt-0 px-1 pt-0">
						<v-card-subtitle class="font-weight-bold mt-1 pt-1">
							{{ deal.end_time }}
						</v-card-subtitle>
						<v-spacer></v-spacer>
						<v-btn class="mt-0 pt-0" text>
							<v-icon small>mdi-map-marker</v-icon>200 m
						</v-btn>
						<v-card-text class="py-0">
							{{ deal.description }}
						</v-card-text>
					</v-layout>

					<v-card-actions class="pt-0 pb-0 mb-0 mt-0">
						<v-spacer></v-spacer>

						<v-btn
							class="pt-0 pb-0 mt-n1 mb-1"
							text
							large
							block
							right
							@click.native="deal.show = !deal.show"
						>
							<v-icon>{{
								deal.show ? 'mdi-chevron-up' : 'mdi-chevron-down'
							}}</v-icon>
						</v-btn>
					</v-card-actions>

					<v-expand-transition>
						<div v-show="deal.show">
							<v-layout row class="mx-3 px-1 mb-0 pb-0">
								<v-card-text class="mt-n1.5 pt-0">
									<v-span class="font-weight-bold">Disclaimer</v-span>
									<br />
									{{ deal.disclaimer }}
								</v-card-text>
								<v-layout row class="d-flex justify-space-around">
									<v-btn
										width="35vw"
										dark
										color="#DFA937"
										tile
										class="buttons"
										depressed
										@click.stop="deal.dialog = true"
									>
										get coupon
									</v-btn>
									<v-dialog v-model="deal.dialog" max-width="290">
										<v-card>
											<v-layout row class="mx-auto">
												<v-card-title class="headline">Success!</v-card-title>
												<v-spacer></v-spacer>
												<v-btn icon @click="deal.dialog = false">
													<v-icon>mdi-close</v-icon>
												</v-btn>
											</v-layout>
											<v-card-text>
												You have successfully claimed this deal! Make sure you
												read the disclaimer and note the time when the coupon
												can be claimed.
											</v-card-text>

											<v-card-actions class="d-flex justify-center pb-3">
												<v-btn
													width="80%"
													dark
													color="#DFA937"
													tile
													class="buttons"
													depressed
													to="/profile"
												>
													see in profile
												</v-btn>
											</v-card-actions>
										</v-card>
									</v-dialog>
									<v-btn width="35vw" tile class="buttonst" depressed>
										share
									</v-btn>
								</v-layout>
							</v-layout>
							<v-divider class="my-5"></v-divider>

							<v-layout row class="mx-5">
								<v-list-item>
									<v-list-item-avatar size="54" color="grey">
										<img src="../assets/avatar.png" alt="John" />
									</v-list-item-avatar>
									<v-list-item-content>
										<v-list-item-title class="headline">{{
											deal.vendor_name
										}}</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-btn text class="pb-0 mb-n3">
									<v-span class="font-weight-bold body">{{
										deal.vendor_address
									}}</v-span>

									<v-icon class="ml-12" right>mdi-map</v-icon>
								</v-btn>
								<v-card-text class="mb-3">
									{{ deal.description }}
								</v-card-text>
							</v-layout>
							<v-img src="../assets/storefront.jpg" height="300px"></v-img>
						</div>
					</v-expand-transition>
				</v-card>
			</v-flex>
		</v-layout>
	</v-container>
</template>

<script>
	import axios from 'axios';
	export default {
		name: 'DealDetails',
		//  mounted(){
		// this.addShow()
		//  },
		//  methods: {
		// addShow() {
		// 	this.details = this.details.map(details => ({
		// 		...details,
		// 		show: false
		// 	}))
		// }
		//  },
		created() {
			axios
				.get('http://localhost:3000/api/v1/promotions.json')
				.then(response => {
					this.details = response.data.cards;
					this.details = this.details.map(details => ({
						...details,
						show: false,
						dialog: false
					}));
				})
				.catch(e => {
					this.error.push(e);
				});
		},
		data() {
			return {
				details: []
			};
		}
	};
</script>

<style scoped>
	.buttons {
		border-radius: 5px;
	}
	.buttonst {
		border-radius: 5px;
		background-color: rgba(223, 169, 55, 20%) !important;
		color: #dfa937 !important;
	}
</style>
