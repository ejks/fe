<template>
	<div class="vendorcard">
    <v-layout row class="mx-auto">
      <v-card tile
              class="mb-6"
              width="85vw"
              xs12 md6 lg4
              v-for="(deal, index) in details"
              :key="deal.id">		
        <v-img src="../assets/cross.jpg"
              height="200px">
        </v-img>
        <v-layout row class="mx-3 px-1 mb-0 pb-0">
          <v-card-title class="mb-0 pb-0">
            {{deal.title}}
          </v-card-title>
        </v-layout>

        <v-layout row class="ml-3 mr-3 mt-0 px-1 pt-0">
          <v-card-subtitle class="font-weight-bold mt-1 pt-1">
            {{deal.time1}}
          </v-card-subtitle>
          <v-spacer></v-spacer>
          <v-card-text class="py-0">
            {{deal.description}}
          </v-card-text>
          <v-card-text class="mt-2 pt-0">
            <v-span class="font-weight-bold">
              Disclaimer
            </v-span>
            <br>
            {{deal.disclaimer}}
          </v-card-text>
          <v-row justify="space-around" class="mx-2 align-center">
            <v-switch inset @change="deal.dialog3 = true" color="success"></v-switch>
            <v-dialog v-model="deal.dialog3"
                      max-width="290">
              <v-card>
                <v-layout row class="mx-auto">
                  <v-card-title class="headline">Activate deal</v-card-title>
                  <v-spacer></v-spacer>
                    <v-btn icon @click="deal.dialog3 = false">
                      <v-icon>mdi-close</v-icon>
                    </v-btn>
                </v-layout>

                <v-form ref="form"
                        v-model="valid"
                        lazy-validation
                        class="mx-5">
                  <v-checkbox v-model="allday"
                              color="green">
                    <template v-slot:label>
                      <div>
                        All day deal
                      </div>
                    </template>
                  </v-checkbox>
                  <v-text-field v-model="start"
                              label="Start-time"
                              required
                              color="#DFA937">
                  </v-text-field>
                  <v-text-field v-model="end"
                                label="End-time"
                                required
                                color="#DFA937">
                  </v-text-field>
                </v-form>

                <v-card-actions class="d-flex justify-space-around pb-3">
                  <v-btn
                    width="90%" dark color="#DFA937" tile class="buttons" depressed @click="deal.dialog3 = false, snackbar = true">
                    save & post
                  </v-btn>
                  <v-snackbar v-model="snackbar" color="success">
                    You have successfully activated this deal. It is now live and is viseble for customers!
                    <v-btn vertical text dark
                          @click="deal.snackbar = false">
                      close
                    </v-btn>
                  </v-snackbar>
                </v-card-actions>
              </v-card>
            </v-dialog>

            <v-btn fab text @click="deal.dialog2 = true">
              <v-icon right>mdi-pencil</v-icon>
            </v-btn>

            <v-dialog v-model="deal.dialog2"
                      max-width="290">
              <v-card>
                <v-layout row class="mx-auto">
                  <v-card-title class="headline">Edit deal</v-card-title>
                  <v-spacer></v-spacer>
                  <v-btn icon @click="deal.dialog2 = false">
                    <v-icon>mdi-close</v-icon>
                  </v-btn>
                </v-layout>
                <v-form ref="form"
                        v-model="valid"
                        lazy-validation
                        class="mx-5">

                  <v-text-field v-model="title"
                                label="Title"
                                required
                                color="#DFA937">
                  </v-text-field>
                  <v-textarea v-model="description"
                              color="#DFA937">
                    <template v-slot:label>
                      <div>
                        Description 
                      </div>
                    </template>
                  </v-textarea>
                  <v-checkbox v-model="allday"
                              color="green">
                    <template  v-slot:label>
                      <div>
                        All day deal
                      </div>
                    </template>
                  </v-checkbox>
                  <v-text-field v-model="start"
                                label="Start-time"
                                required
                                color="#DFA937">
                  </v-text-field>
                  <v-text-field v-model="end"
                                label="End-time"
                                required
                                color="#DFA937">
                  </v-text-field>
                  <!-- <v-text-field
                    v-model="photo"
                    label="Deal Photo"
                    color="#DFA937"
                    append-icon="mdi-camera-plus"
                  ></v-text-field> -->
                  <v-file-input label="Deal Photo"
                                prepend-icon="mdi-camera">
                  </v-file-input>
                </v-form>

                <v-card-actions class="d-flex justify-space-around pb-3">
                  <v-btn
                    width="50%" dark color="#DFA937" tile class="buttons" depressed @click="deal.dialog2 = false">
                    save & post
                  </v-btn>
                  <v-btn
                    width="40%" dark color="#DFA937" tile class="buttonst" depressed @click="deal.dialog2 = false">
                    save
                  </v-btn>
                  <v-snackbar v-model="snackbar">
                    You have successfully edited this deal. Toggle the switch to make the deal live and visable for customers!
                    <v-btn color="success"
                          vertical
                          text
                          dark
                          @click="deal.snackbar = false">
                      close
                    </v-btn>
                  </v-snackbar>
                </v-card-actions>
              </v-card>
            </v-dialog>

            <v-btn fab text @click="deal.dialog = true">
              <v-icon right>mdi-delete</v-icon>
            </v-btn>

            <v-dialog v-model="deal.dialog"
                      max-width="290">
              <v-card>
                <v-layout row class="mx-auto">
                  <v-card-title class="headline">Delete Deal</v-card-title>
                  <v-spacer></v-spacer>
                  <v-btn icon @click="deal.dialog = false">
                    <v-icon>mdi-close</v-icon>
                  </v-btn>
                </v-layout>

                <v-card-text>
                  Are you sure you want to cancel this deal? This action is permanent.
                </v-card-text>

                <v-card-actions class="d-flex justify-center pb-3">
                  <v-btn width="80%" dark color="#DFA937" tile class="buttons" depressed @click="remove(index)">
                    yes, i am sure
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>

            <v-snackbar v-model="snackbar">
              You have successfully activated this deal. It is now live and is viseble for customers!
              <v-btn color="success"
                      vertical
                      text
                      dark
                      @click="snackbar = false">
                close
              </v-btn>
            </v-snackbar>
          </v-row>	
        </v-layout>
      </v-card>
    </v-layout>
	</div>
</template>

<script>
export default {
  name: "VendorCard",
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
 methods: {
		remove(id) {
			// this.deals.splice(id, 1); JavaScript
			// below VueJS delete helper
			this.$delete(this.details, id);
		}

	},
	data: () => ({
		snackbar: false,
      details: [
          { id: 1, src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Stickstick", title: "50% off Chicken Skewers", time1: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks at our Xuhui location. Share this deal  with your friends and enjoy it together.", distance: "300 m", disclaimer: "Offer only applies to individuals who have claimed the deal through Gast. Limit of 5 skewers per person. Offer is on between 20.00 - 22.00.", address: "Xinhua Rd, No 245, Xuhui", dialog: false, switch: false, dialog2: false, dialog3: false},
		{ id: 2, src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Bones", title: "Buy one get one Rib racks", time1: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks..", distance: "200 m", disclaimer: "Offer only applies to individuals who have claimed the deal through Gast. Limit of 5 skewers per person. Offer is on between 20.00 - 22.00.", dialog: false, switch: false, dialog2: false, dialog3: false},
		{ id: 3, src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg", restaurant: "Cocola", title: "75% off all cakes", time1: "All day offer", description: "We have some extra chicken that needs to go today. Come enjoy some skewers and drinks..", distance: "100 m", disclaimer: "Offer only applies to individuals who have claimed the deal through Gast. Limit of 5 skewers per person. Offer is on between 20.00 - 22.00.", dialog: false, switch: false, dialog2: false, dialog3: false}
        ]
    })
}
</script>
<style scoped>
.buttons {
	border-radius: 5px;
}
.buttonst {
	border-radius: 5px;
	background-color: rgba(223, 169, 55, 20%)!important;
	color: #DFA937!important;
}
</style>