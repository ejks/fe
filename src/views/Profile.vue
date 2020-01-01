<template>
	<div class="profile">
		<v-img height="200px" src="../assets/cross.jpg">
		</v-img>
		<v-layout row class="mx-5 my-5">
			<v-list-item>
			<v-list-item-avatar size="54" color="grey">
				<img
        src="../assets/avatar.png"
        alt="John"
      >
			</v-list-item-avatar>
			<v-list-item-content>
				<v-list-item-title class="headline">Jim Halpert</v-list-item-title>
			</v-list-item-content>
		</v-list-item>
		<h3 class="mx-4 mt-3">Today's claims</h3>
		<v-list two-line>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title>50% off Chicken Wings</v-list-item-title>
          <v-list-item-subtitle>All day offer</v-list-item-subtitle>
        </v-list-item-content>

        <v-list-item-icon class="ma-0">
			<v-btn fab text>
          <v-icon>mdi-delete</v-icon>
      </v-btn>
        </v-list-item-icon>
      </v-list-item>
  </v-list>
		</v-layout>
		<v-layout justify-center>
			<v-btn
            width="80%" dark color="cyan darken-3" rounded depressed class="mb-5" to="/deals"
          >
            browse deals
          </v-btn>
		</v-layout>
		
	</div>
</template>

<style scoped>
* {
	background-color: white;
}

</style>