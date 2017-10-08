<template>
  <div class="tile is-ancestor">
    <div class="tile is-parent">
      <article class="tile is-child">
      </article>
    </div>
    <div class="tile is-parent is-10">
      <article class="tile is-child box">
        <div class="tabs is-fullwidth ">
          <ul>
            <li>
                <span class="title">{{business}}</span>
            </li>
            <li>
                <span class="title">{{transactions}} purchases</span>
            </li>
            <li>
                <span class="title">${{totalSpent}}</span>
            </li>
          </ul>
        </div>
        <div class="button-collection">
          <a class="button is-large is-danger" @click="launchModal(ignore)">Ignore</a>
          <a class="button is-large is-warning" @click="launchModal(snooze)">Snooze</a>
          <a class="button is-large is-success" @click="launchModal(whittle)">Whittle this!</a>
        </div>

      </article>
    </div>
    <div class="tile is-parent">
      <article class="tile is-child">
      </article>
    </div>
    <ConfirmationModal @actionConfirmed="sendRequest" @actionDenied="resetModal" v-if="showModal" :modalType="modalType" :business="business"></ConfirmationModal>
  </div>
</template>

<script>
import axios from 'axios'
import ConfirmationModal from './ConfirmationModal'

export default {
  name: 'TransactionWidget',
  components: {ConfirmationModal},
  props: {
    transaction: Object
  },
  data () {
    return {
      business: this.transaction.business,
      transactions: this.transaction.transactions,
      totalSpent: this.transaction.total_spent,
      showModal: false,
      modalType: "",
      ignore: "ignore",
      snooze: "snooze",
      whittle: "whittle"
    }
  },
  methods: {
    launchModal: function (type) {
      this.modalType = type
      this.showModal = true
    },
    sendRequest: function (business, actionType) {
      console.log(business, actionType)
      this.modalType = ""
      this.showModal = false
    },
    resetModal: function () {
      this.modalType = ""
      this.showModal = false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
  @import '~bulma'

</style>
