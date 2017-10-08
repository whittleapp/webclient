<template>
    <div class="container">
      <div class="notification">
        <TransactionWidget v-for="transaction in realTransactions" :transaction="transaction"></TransactionWidget>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import TransactionWidget from './TransactionWidget'

export default {
  name: 'Feed',
  components: {TransactionWidget},
  data () {
    return {
      realTransactions: []
    }
  },

  // Fetches transactions when the component is created.
  created() {
    axios.get(`http://localhost:3000/businesses`)
    .then(response => {
      this.realTransactions = response.data.summary
    })
    .catch(e => {
      console.log('You fucked up!')
      // this.errors.push(e)
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
  @import "../assets/styles/app.sass"

  div
    font-family: $family-primary
</style>
