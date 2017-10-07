<template>
  <div>
  	<div class="modal is-active">
		  <div class="modal-background"></div>
		  <div class="modal-content">
		    <p>{{message}}</p>
		  </div>
		  <button class="modal-close is-large" aria-label="close"></button>
		</div>
  </div>
</template>

<script>

export default {
  name: 'ConfirmationModal',
  props: {
  	modalType: String
  },
  data () {
  	return {
  		messageOptions: {
  			ignore: "We will ignore transactions with this business in the future",
  			snooze: "We will remind you about this spending habbit later",
  			whittle: "Great! We will transfer future savings from reductions in this spending habbit to your savings account!"
  		},
  		messageKey: this.modalType
  	}
  },
  computed:  
}
</script>

<style lang="sass" scoped>
  @import '~bulma'

</style>
