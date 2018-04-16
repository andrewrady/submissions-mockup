<template>
  <div class="ui fluid styled accordion submission">
    <div class="ui title">
      <div class="ui equal width grid">
        <div class="row">
          <div class="four wide column">
            {{ client.client.firstName }} {{ client.client.lastName }}
            <i class="olive checkmark icon"></i>
          </div>
          <div class="two wide column">
            <span>Date</span>
            4/1/2018
          </div>
          <div class="column">
            <span>Status
              <i class="ui circular tiny empty label negative"></i>
            </span><br> Completed
          </div>
          <div class="column">
            <span>Submiied by
              <i class="ui circular tiny empty label positive"></i>
            </span><br> Kevin H.
          </div>
          <div class="one wide middle aligned column">
            <i class="small circular inverted yellow edit icon" @click="toggleContent()"></i>
          </div>
        </div>
      </div>
    </div>
    <div v-show="showContent" class="ui divider"></div>
    <div class="animation-container">
      <transition name="slide-down">
        <div v-show="showContent" class="ui content">
          <div class="ui equal width grid">
            <div class="row">
              <div class="five wide column">
                <span>Address</span><br> {{ client.billingAddress.street }}
              </div>
              <div class="column">
                <span>City</span><br> {{ client.billingAddress.state }}
              </div>
              <div class="column">
                <span>State</span><br> {{ client.billingAddress.county }}
              </div>
              <div class="column">
                <span>zip</span><br> {{ client.billingAddress.zip }}
              </div>
            </div>
            <div class="ui divider"></div>
            <div class="row">
              <div class="column">
                <span>Card Type</span><br> {{ client.billingInformation.cardType }}
              </div>
              <div class="column">
                <span>Card # (last 4)</span><br> {{ client.billingInformation.cardNumber }}
              </div>
              <div class="column">
                <span>Experation</span><br> {{ client.billingInformation.experationMonth }} / {{ client.billingInformation.experationYear }}
              </div>
              <div class="column">
                <span>CVC</span><br> {{ client.billingInformation.cvc }}
              </div>
            </div>
          </div>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  name: 'client-info',
  props: ['client'],
  data() {
    return {
      showContent: false
    }
  },
  methods: {
    toggleContent() {
      this.showContent = !this.showContent;
    },
  }
}
</script>
