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
          <div class="field" v-if="step == 1">
            <label>First Name</label>
            <input type="text" v-model="form.client.firstName" rel="test" @keydown="nextField">
          </div>
          <div class="field" v-if="step == 2">
            <label>Last Name</label>
            <input type="text" v-model="form.client.lastName" rel="test" @keydown="nextField">
          </div>

          <div class="field" v-if="step == 3">
            <label>Street Address</label>
            <input type="text" v-model="form.billingAddress.street" autofocus @keydown="nextField">
          </div>
          <div class="field" v-if="step == 4">
            <label>Apt #</label>
            <input type="text" v-model="form.billingAddress.apt" @keydown="nextField">
          </div>
          <div class="field" v-if="step == 5">
            <label>State</label>
            <input type="text" v-model="form.billingAddress.state" @keydown="nextField">
          </div>
          <div class="field" v-if="step == 6">
            <label>County</label>
            <input type="text" v-model="form.billingAddress.county" @keydown="nextField">
          </div>

          <div class="field" v-if="step == 7">
            <label>Card Type</label>
            <select v-model="form.billingInformation.cardType" @change="nextField">
              <option value="Visa">Visa</option>
              <option value="Visa">American Express</option>
              <option value="Visa">Discover</option>
              <option value="Visa">Master Card</option>
            </select>
          </div>
          <div class="field" v-if="step == 8">
            <label>Card Number</label>
            <input type="text" v-model="form.billingInformation.cardNumber" @keydown="nextField">
          </div>
          <div class="field" v-if="step == 9">
            <label>CVC</label>
            <input type="text" v-model="form.billingInformation.cvc" @keydown="nextField">
          </div>
          <div class="field" v-if="step == 10">
            <label>Experation Month</label>
            <select class="ui fluid search dropdown" name="card[expire-month]" v-model="form.billingInformation.experationMonth" @change="nextField">
                  <option value="">Month</option>
                  <option value="1">January</option>
                  <option value="2">February</option>
                  <option value="3">March</option>
                  <option value="4">April</option>
                  <option value="5">May</option>
                  <option value="6">June</option>
                  <option value="7">July</option>
                  <option value="8">August</option>
                  <option value="9">September</option>
                  <option value="10">October</option>
                  <option value="11">November</option>
                  <option value="12">December</option>
                </select>
          </div>
          <div class="field" v-if="step == 11">
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
      this.setFocus();

    },
    decreaseStep() {
      if (this.step >= 2)
        this.step--
      this.decreasePrecentage()
      this.setFocus();
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
    },
    setFocus() {
      let test = document.getElementsByClassName('field')[0]
      let input = test.querySelector('input')
      this.$nextTick(() => {
        input.focus();
      })
    }
  }
}
</script>