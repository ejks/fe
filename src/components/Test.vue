<template>
<div id="app">
  <v-app id="inspire">
    <v-container fluid>
      <v-flex>
        <v-layout row wrap>
          <v-flex v-for="person in newPeople" :key="person.md5" xs12 sm4 md4 mr-4 mb-5>
            <v-card color="white" class="blue-grey--text elevation-0">
              <v-container fluid grid-list-lg>
                <v-layout row>
                  <v-flex xs7>
                    <div>
                      <div class="headline"><b>{{ person.name.first }} {{ person.name.last}}</b></div>
                      <div><b>User: </b>{{ person.login.username }}</div>
                      <div><b>Address: </b>{{ person.location.street }}</div>
                      <div><b>City: </b>{{ person.location.city }}</div>
                      <div><b>State: </b>{{ person.location.state }}</div>
                    </div>
                  </v-flex>
                  <v-flex xs5>
                    <v-card-media
                      :src="person.picture.large"
                      height="125px"
                      contain
                    ></v-card-media>
                  </v-flex>
                </v-layout>
              </v-container>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn flat color="blue-grey darken-4" @click.native="person.show = !person.show">View personal data</v-btn>
              
              </v-card-actions>
              <v-slide-y-transition>
                <v-card-text v-show="person.show">
                  <div class="text-lg-right"><b>DOB: </b>{{ person.dob }}</div>
                  <div class="text-lg-right"><b>Registered: </b>{{ person.registered }}</div>
                  <div class="text-lg-right"><b>Phone: </b>{{ person.phone }}</div>
                  <div class="text-lg-right"><b>Cell: </b>{{ person.cell }}</div>
                </v-card-text>
              </v-slide-y-transition>
          </v-card>
          </v-flex>
        </v-layout>
      </v-flex>
    </v-container>
  </v-app>
</div>
</template>
<script>
  export default {
mounted(){
    this.addShow()
  },
  methods: {
    addShow() {
      this.newPeople = this.people.map(people => ({
        ...people,
        show: false
      })) 
    }
  },
  data: () => ({
    newPeople: [],
    people: [

]
  })
  }
  
</script>

<script>
export default {

}
</script>