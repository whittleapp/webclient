<template>
    <div class="container">
      <div class="notification">
        <TransactionWidget v-for="object in dummyCollection" :transaction="object"></TransactionWidget>
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
      dummyCollection: [{seller: 'Starbucks', transactions: 15, totalSpent: 85}, {seller: 'Netflix', transactions: 1, totalSpent: 12}, {seller: 'Safeway', transactions: 6, totalSpent: 500}],
      realTransactions: []
    }
  },

  // Fetches transactions when the component is created.
  created() {
    axios.get(`http://localhost:3000/transactions`)
    // axios.get(`http://jsonplaceholder.typicode.com/posts`)
    .then(response => {
      // JSON responses are automatically parsed.
      this.realTransactions = response.data
      console.log(response.data);
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
  @import '~bulma'

</style>
