<template>
  <v-app>
    <Navbar />
    <!-- <GetStartedBtn /> -->
    <!-- <DealCard /> -->
    <v-content>
      <router-view></router-view>
      
    </v-content>

  </v-app>
</template>

<script>
import Navbar from '@/components/Navbar';

// import ClickCounter from '@/components/ClickCounter';

// import GetStartedBtn from '@/components/GetStartedBtn';
// import DealCard from '@/components/DealCard';

export default {
  name: 'App',
  components: { Navbar },


}
</script>
<style>
.v-content {
  padding:0!important;
}
</style>
