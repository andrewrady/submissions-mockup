<template>
  <div class="ui modal">
    <i class="close icon" @click="exit"></i>
    <div class="header">
      <div v-if="step < 3">Shipping Information</div>
      <div v-if="step <= 6 && step >= 3">Billing Address</div>
      <div v-if="step > 6 ">Billing Information</div>
    </div>
    <div class="content top attached">
      <div class="description">
        <form class="ui form" @submit.prevent>
          <div class="field" v-show="step == 1">
            <label>First Name</label>
            <input type="text" v-model="form.client.firstName" autofocus @keydown="nextField">
          </div>
          <div class="field" v-show="step == 2">
            <label>Last Name</label>
            <input type="text" v-model="form.client.lastName" autofocus @keydown="nextField">
          </div>

          <div class="field" v-show="step == 3">
            <label>Street Address</label>
            <input type="text" v-model="form.billingAddress.street" autofocus @keydown="nextField">
          </div>
          <div class="field" v-show="step == 4">
            <label>Apt #</label>
            <input type="text" v-model="form.billingAddress.apt" @keydown="nextField">
          </div>
          <div class="field" v-show="step == 5">
            <label>State</label>
            <input type="text" v-model="form.billingAddress.state" @keydown="nextField">
          </div>
          <div class="field" v-show="step == 6">
            <label>County</label>
            <input type="text" v-model="form.billingAddress.county" @keydown="nextField">
          </div>

          <div class="field" v-show="step == 7">
            <label>Card Type</label>
            <input type="text" v-model="form.billingInformation.cardType" @keydown="nextField">
          </div>
          <div class="field" v-show="step == 8">
            <label>Card Number</label>
            <input type="text" v-model="form.billingInformation.cardNumber" @keydown="nextField">
          </div>
          <div class="field" v-show="step == 9">
            <label>CVC</label>
            <input type="text" v-model="form.billingInformation.cvc" @keydown="nextField">
          </div>
          <div class="field" v-show="step == 10">
            <label>Experation Month</label>
            <input type="text" v-model="form.billingInformation.experationMonth" @keydown="nextField">
          </div>
          <div class="field" v-show="step == 11">
            <label>Experation Year</label>
            <input type="text" v-model="form.billingInformation.experationYear" @keydown="nextField">
          </div>
        </form>
      </div>
    </div>
    <div class="ui bottom attached progress">
      <div class="bar"></div>
    </div>
    <div class="actions">
      <div class="ui black deny button" @click="decreaseStep" v-if="step >= 2">
        Back
      </div>
      <div class="ui positive right button" @click="increaseStep" v-if="step <= 10">
        Next
      </div>
      <div class="ui blue right button" @click="exit" v-if="step == 11">
        Done
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'modal',
  props: ['form'],
  data() {
    return {
      step: 1,
      precent: 12
    }
  },
  methods: {
    exit() {
      this.$emit('keyEntryMode')
    },
    increaseStep() {
      if (this.step < 12)
        this.step++
        this.increasePrecentage();
    },
    decreaseStep() {
      if (this.step >= 2)
        this.step--
        this.decreasePrecentage()
    },
    nextField(e) {
      if (e.keyCode == 9)
        this.increaseStep();
    },
    increasePrecentage() {
      let bar = document.getElementsByClassName('bar')[0];
      this.precent = this.precent + 8.8;
      bar.style.width = this.precent + '%';
    },
    decreasePrecentage() {
      let bar = document.getElementsByClassName('bar')[0];
      this.precent = this.precent - 8.8;  
      bar.style.width = this.precent + '%';
    }
  }
}
</script>