<template>
  <div id="ms-guide">
    <Dashboard />
    <Explanation />
    <Feature />
    <Supporters />
    <SubmitFeedback />
    <Footer />
  </div>
</template>

<script>
  export default {
    name: 'HomePage'
  }
</script>

<style lang="stylus">
@import "../config.styl"

#ms-guide
  color black
  .wrap-content 
    width 75%
    margin 0 auto
  .flex-container
    display flex
    flex-direction row
  h1
    font-size 4.2rem
    font-weight bold
  p
    font-size $lnSize
    font-weight 400
  .round-button 
    display flex
    padding 0.8rem 1.8rem
    background transparent
    color $green
    border 1.5px solid $green
    border-radius 25px
    font-size $inputSize
    outline none
    cursor pointer
    font-weight bold
    &:hover
      background-color $green
      color #000

@media screen and (max-width: $SCLarge)
  #ms-guide
    h1
      font-size 2.8rem
</style>
