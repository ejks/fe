<template>
	<div class="home mb-12 pb-5">
		<Navbar />
		<v-img height="200px" src="../assets/cross.jpg">
		</v-img>
		
		<v-layout row class="mx-9 my-8">
			<p class="font-weight-medium text-center">Find deals on food that needs to be consumed today!</p>

			<v-btn dark block color="#DFA937" tile class="buttons" depressed @click="dialog1 = true">
				user login to find deals
				<v-icon right>mdi-wechat</v-icon>
			</v-btn>
			<v-dialog v-model="dialog" max-width="300">
				<v-card>
					<v-layout row class="mx-3">
						<v-card-title>Login</v-card-title>
				<v-form
    ref="form"
    v-model="valid"
    lazy-validation
    class="mx-5"
  >

    <v-text-field
      v-model="email"
      :rules="emailRules"
      label="E-mail"
      required
      color="#DFA937"
    ></v-text-field>
	
	<v-text-field
        v-model="password"
        :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
        :type="show1 ? 'text' : 'password'"
        name="input-10-1"
        @click:append="show1 = !show1"
        color="#DFA937"
    ></v-text-field>
  </v-form>
  <v-btn dark width="95%" color="#DFA937" tile class="buttons mb-3" depressed to="/vendor">
				login
			</v-btn>
			<v-btn text small class="pt-0 mt-0" @click="dialog1 = true">
			<v-card-text class="mr-3 pt-0 text-lowercase"><span class="text-capitalize">Don’t</span> have an account yet? <span class="font-weight-bold"><span class="text-capitalize">Register</span> here</span></v-card-text>
		</v-btn>
</v-layout>
</v-card>
</v-dialog>
<v-dialog v-model="dialog1" max-width="300">
				<v-card>
					<v-layout row class="mx-3">
						<v-card-title>Register Vendor Account</v-card-title>
				<v-form
    ref="form"
    v-model="valid"
    lazy-validation
    class="mx-5"
  >

    <v-text-field
      v-model="vendorname"
      label="Name of Establishment"
      required
      color="#DFA937"
    ></v-text-field>

    <v-select
            v-model="value"
            :items="items"
            attach
            label="Type of Establishment"
            color="#DFA937"
    ></v-select>

    <v-text-field
      v-model="contactperson"
      label="Contact Person"
      required
      color="#DFA937"
    ></v-text-field>

    <v-text-field
      v-model="email"
      label="E-mail"
      
      required
      color="#DFA937"
    ></v-text-field>
	
	<v-text-field
      v-model="contactnumber"
      label="Phone Number"
      
      required
      color="#DFA937"
    ></v-text-field>

	<v-text-field
        v-model="password"
        :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
        :type="show1 ? 'text' : 'password'"
        name="input-10-1"
        label="Password"
        @click:append="show1 = !show1"
        color="#DFA937"
    ></v-text-field>
    <v-text-field
        v-model="password"
        :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
        :type="show1 ? 'text' : 'password'"
        label="Confirm Password"
        name="input-10-1"
        @click:append="show1 = !show1"
        color="#DFA937"
    ></v-text-field>
    
	
		
  </v-form>
  <v-btn dark width="95%" color="#DFA937" tile class="buttons mb-3" depressed @click="snackbar = true">
				submit for approval
			</v-btn>
			<v-snackbar
			v-model="snackbar" color="success">
			Successfully submitted. An account manager will contact you shortly to confirm your account
			<v-btn
			vertical
			text
			dark
			@click="snackbar = false">close</v-btn>
			</v-snackbar>

			<v-btn text small class="pt-0 mt-0" @click="dialog = true">
			<v-card-text class="mr-3 pt-0 text-lowercase"><span class="text-capitalize">Already</span> have an account? <span class="font-weight-bold"><span class="text-capitalize">Login</span> here</span></v-card-text>
		</v-btn>
</v-layout>
</v-card>
			</v-dialog>
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
// import Gast from '../assets/rac1.svg'
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
.log {
	width: 10rem;
	height: 10rem;
}
</style>