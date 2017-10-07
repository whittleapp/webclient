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
      dummyCollection: [{seller: 'Starbucks', transactions: 15, totalSpent: 85}, {seller: 'Netflix', transactions: 1, totalSpent: 12}, {seller: 'Safeway', transactions: 6, totalSpent: 500}]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
  @import '~bulma'
  
</style>
