<template>
    <div class="container">
      <div class="notification">
        <TransactionWidget @widgetRemoved="reRender" v-for="(transaction, index) in realTransactions" :transaction="transaction" :index="index"></TransactionWidget>
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
  methods: {
    reRender: function (ind) {
      this.realTransactions.splice(ind, 1)
      console.log("*******************")
      console.log(ind)
    }
  },
  // Fetches transactions when the component is created.
  created() {
    axios.get(`http://localhost:3000/businesses`)
    .then(response => {
      this.realTransactions = response.data.summary
      console.log(this.realTransactions)
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
