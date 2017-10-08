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
                <span class="title">{{seller}}</span>
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
          <a class="button is-large is-danger">Ignore</a>
          <a class="button is-large is-warning">Snooze</a>
          <a class="button is-large is-success">Whittle this!</a>
        </div>

      </article>
    </div>
    <div class="tile is-parent">
      <article class="tile is-child">
      </article>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'TransactionWidget',
  props: {
    transaction: Object
  },
  data () {
    return {
      seller: this.transaction.seller,
      transactions: this.transaction.transactions,
      totalSpent: this.transaction.totalSpent
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
  @import '~bulma'

  .button-collection


</style>
