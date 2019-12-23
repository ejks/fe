<template>
  <v-app>
    <Navbar />
    <Carousel />
    <!-- <GetStartedBtn /> -->
    <!-- <DealCard /> -->
    <v-content>
      <router-view></router-view>
      
    </v-content>

  </v-app>
</template>

<script>
import Navbar from '@/components/Navbar';
import Carousel from '@/components/Carousel';
// import ClickCounter from '@/components/ClickCounter';

// import GetStartedBtn from '@/components/GetStartedBtn';
// import DealCard from '@/components/DealCard';

export default {
  name: 'App',
  components: { Navbar, Carousel },


}
</script>
<style>

</style>
