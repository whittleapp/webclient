<template>
  <div class="background">
    <section class="hero is-small is-dark">
      <div class="hero-body">
        <div class="container has-text-centered">
          <h1 class="title">Whittle</h1>
        </div>
      </div>
    </section>
    <Feed></Feed>
  </div>
</template>

<script>
import Feed from './Feed'

export default {
  name: 'FeedPage',
  components: {Feed},
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
  @import '~bulma'

  .background
    background: $info
    position: absolute
    min-height: 100%
    width: 100%

  
</style>
