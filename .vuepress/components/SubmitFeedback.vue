<template>
  <div class="feedback">
    <div class="wrap-content">
      <h1 id="feedback">Get Involved</h1>
      <p>
        Do you have feedback, questions or an inquiry to support the OMG standard?<br />
        Reach out to us.
      </p>
      <form name="contact" method="POST" @submit.prevent="handleSubmit">
        <div>
          <input v-model="form.email" required type="email" name="email" placeholder="Email">
        </div>
        <div>
          <textarea v-model="form.message" name="message" rows="7" cols="50" placeholder="Message (optional)"></textarea>
        </div>
        <div>
          <button :disabled="form.sending" class="round-button" type="submit">Send</button>
        </div>
        <div class="contact-messages">
          <div v-if="form.sent" class="contact-message">
            <p><b>Thank you!</b> We'll get in touch with you shortly</p>
            <span class="close" @click="form.sent = false">&times;</span>
            <!-- <micro-modal text="<h3>Thank you !</h3><p>We'll get in touch with you shortly</p>" @close="form.sent = false" /> -->
          </div>
          <div v-if="form.error" class="contact-message error">
            <p><b>Error !</b> Please, try again</p>
            <span class="close" @click="form.error = false">&times;</span>
            <!-- <micro-modal text="<h3>Error !</h3><p>Please, try again</p>" @close="form.error = false" /> -->
          </div>
        </div>
      </form>
    </div>
    <div class="feedback-img" />
  </div>
</template>

<script>
import MicroModal from './MicroModal'

export default {
  name: 'SubmitFeedback',
  components: { MicroModal },
  data: () => ({
    form: {
      email: '',
      message: '',
      sent: false,
      error: false,
      sending: false
    }
  }),
  methods: {
    handleSubmit: function () {
      this.form.error = false
      this.form.sent = false
      this.form.sending = true
      fetch('/', {
        method: 'POST',
        headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
        body: `form-name=contact&email=${encodeURIComponent(this.form.email)}&message=${encodeURIComponent(this.form.message)}`
      }).then((res) => {
        if (res.status !== 200) {
          this.form.error = true
        } else {
          this.form.sent = true
        }
        this.form.sending = false
      })
    }
  }
}
</script>

<style lang="stylus" scoped>
@import "../config.styl"

.contact-messages
  margin-top 3rem

.contact-message.error
  border-color #F82E2E
  color #F82E2E
  p
    color #F82E2E

.contact-message
  width 460px
  max-width 80%
  border-width 1px
  border-style solid
  border-color $green
  border-radius .75rem
  padding 0.5rem 1.5rem
  margin 1rem 0
  position relative
  color $green
  .close
    position absolute
    right 1rem
    height 100%
    top 0
    align-items center
    display flex
    font-size 1.3rem
    font-weight bold
    cursor pointer
  p
    color $green
    margin .5rem 0 !important
    padding 0

.feedback 
  position relative
  background #111420
  color white
  padding 4rem 0px 5rem 0px
  z-index 2
  &::after
    content ''
    display block
    position absolute
    top 0
    left 0
    width 100%
    height 100%
    background-image -moz-linear-gradient(left, rgba(17, 20, 32, 1) 0%, rgba(17, 20, 32, 1) 50%, rgba(17, 20, 32, 0) 100%)
    background-image -webkit-linear-gradient(left, rgba(17, 20, 32, 1) 0%,rgba(17, 20, 32, 1) 50%,rgba(17, 20, 32, 0) 100%)
    background-image linear-gradient(to right, rgba(17, 20, 32, 1) 0%,rgba(17, 20, 32, 1) 50%,rgba(17, 20, 32, 0) 100%)
    z-index -1
  &::before
    content ''
    display block
    position absolute
    top 0
    left 0
    width 100%
    height 100%
    background-image url('/grid.svg')
    background-size 7% auto
    background-position bottom center
    opacity 0.4
    z-index -1
  input,textarea
    color white
    border 1px solid #41434d!important
    border-radius 6px
    background transparent
    outline none
    padding 0.4rem 1rem
    font-size $inputSize
    font-family inherit
    max-width 90%
    width 460px
    min-width 460px
  textarea
    min-height 150px
    max-height 150px
  h1,p
    margin-bottom 30px
  form div 
    margin-bottom 20px  
  .feedback-img 
    position absolute
    right 0px
    top -10px
    width 600px
    height calc(100% + 10px)
    background-image url('/footer_graphic.svg')
    background-size cover
@media (max-width: $SCMedium)
  html
    font-size 16px
  .feedback
    .feedback-img 
        display none
@media (max-width: $SCMobileNarrow)
  html
    font-size 14px
</style>
