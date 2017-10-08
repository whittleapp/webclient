<template>
	<div class="modal is-active">
	  <div class="modal-background"></div>
	  <div class="modal-card">
	    <section class="modal-card-body">
	      {{message}}
	    </section>
	    <footer class="modal-card-foot">
	      <button @click="okPressed"class="button is-success">Ok!</button>
	      <button @click="undoPressed" class="button is-danger">Undo</button>
	    </footer>
	  </div>
	</div>
</template>

<script>

export default {
  name: 'ConfirmationModal',
  props: ['modalType', 'business'],
  data () {
  	return {
  		messageOptions: {
  			ignore: `We will ignore transactions with ${this.business} in the future`,
  			snooze: `We will remind you about ${this.business} later`,
  			whittle: `Great! We will transfer future savings from reductions in this spending with ${this.business} your savings account!`
  		}
  	}
  },
  computed: {
  	message: function () {
  		let messageKey = this.modalType
  		return this.messageOptions[messageKey]
  	}
  },
	methods: {
		okPressed: function () {
			this.$emit('actionConfirmed', this.business, this.modalType)
		},
		undoPressed: function() {
			this.$emit('actionDenied')
		}
	} 
}
</script>

<style lang="sass" scoped>
  @import '~bulma'

</style>
