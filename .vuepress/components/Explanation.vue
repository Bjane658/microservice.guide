<template>
  <div class="wrap-content">
      <h1>Why OMG?</h1>
      <p>Microservices, by design, are intended to be highly reusable, operational-specific and language-agnostic. This guide defines the standard that defines how to interface with microservices to provide a blueprint for consistency and reusability. By following this documentation, developers     will be able to create a platform that is well-documented and portable while not compromising flexibility.</p>
      <p>The old way of communicating software architecture and design through whiteboards and diagrams is immediately out of date and often becomes difficult to read and understand. By mapping your microservice architecture using pre-defined yaml by OMG, developers are given a way to describe architecture and operational requirements as human-readable structured data.</p>
      <p>Having these models in plain text files gives developers a framework to effectively communicate architecture, service to service communication, and operational complexities to many different audiences.</p>
  </div>
</template>

<script>
  export default {
  }
</script>

<style lang="stylus" scoped>
  @import "../config.styl"
  
  div.wrap-content
    padding 4rem 0 5rem 0
    font-size $lnSize
  p 
    margin-bottom 2rem
    line-height 2.4rem
  h1
    margin-bottom 2.5rem
</style>
