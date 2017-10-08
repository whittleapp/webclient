<template>
  <div v-if="mainFeedShowing" class="tile is-ancestor">
    <div class="tile is-parent">
      <article class="tile is-child">
      </article>
    </div>
    <div class="tile is-parent is-10">
      <article class="tile is-child box">
        <div class="tabs is-fullwidth ">
          <ul>
            <li>
                <span class="subtitle">{{business}}</span>
            </li>
            <li>
                <span class="subtitle">{{transactions}} purchases</span>
            </li>
            <li>
                <span class="subtitle">${{totalSpent}}</span>
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
import qs from 'qs'
import ConfirmationModal from './ConfirmationModal'

export default {
  name: 'TransactionWidget',
  components: {ConfirmationModal},
  props: {
    transaction: Object,
    index: Number
  },
  data () {
    return {
      business: this.transaction.business,
      transactions: this.transaction.transactions,
      totalSpent: this.transaction.total_spent,
      businessID: this.transaction.id,
      showModal: false,
      modalType: "",
      ignore: "ignore",
      snooze: "snooze",
      whittle: "whittle",
      mainFeedShowing: true
    }
  },
  methods: {
    launchModal: function (type) {
      this.modalType = type
      this.showModal = true
    },
    sendRequest: function (actionType) {
      let apiURL = `http://localhost:3000/businesses/${this.businessID}`
      axios.put(apiURL, {
        [actionType]: true
      })
      .then(function (response) {
        console.log(response)
      })
      .catch(function (error) {
        console.log(error);
      })
      this.modalType = ""
      this.showModal = false
      this.mainFeedShowing = false
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

  .button-collection
    display: flex
    align-items: center
    justify-content: center

  .button
    margin: 5px

</style>
