<template>
  <div class="background">
    <section class="hero is-medium is-dark">
      <div class="hero-body">
        <div class="container has-text-centered">
          <h1 class="title">Whittle</h1>
        </div>
      </div>
    </section>
    <div class="container">
      <div class="notification">
        This container is <strong>centered</strong> on desktop.
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FeedPage',
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
