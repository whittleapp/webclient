<template>
	<div class="modal is-active">
	  <div class="modal-background"></div>
	  <div class="modal-card">
	    <section class="modal-card-body">
	      {{message}}
	    </section>
	    <footer class="modal-card-foot">
	      <button class="button is-success">Ok!</button>
	      <button class="button is-danger">Undo</button>
	    </footer>
	  </div>
	</div>
</template>

<script>

export default {
  name: 'ConfirmationModal',
  props: ['modalType', 'seller'],
  data () {
  	return {
  		messageOptions: {
  			ignore: `We will ignore transactions with ${this.seller} in the future`,
  			snooze: `We will remind you about ${this.seller} later`,
  			whittle: `Great! We will transfer future savings from reductions in this spending with ${this.seller} your savings account!`
  		}
  	}
  },
  computed: {
  	message: function () {
  		let messageKey = this.modalType
  		return this.messageOptions[messageKey]
  	}
  } 
}
</script>

<style lang="sass" scoped>
  @import '~bulma'

</style>
