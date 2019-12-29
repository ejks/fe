<template>
	<div>
      <v-btn
        icon
        @click.native="deal.show = !deal.show"
      >
        <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
      </v-btn>
	</div>
</template>

<script>
export default {
	name: "ClickCounter",
	data () {
      return {
        show: false
      }
    } 
};
	
</script>