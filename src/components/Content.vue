<template>
  <div class="ui container app body">
    <!-- agent menu -->
    <div class="ui inverted agent menu">
      <div class="right padded menu">
        <a class="item active" data-tab="tab-agent-detail">
          Submissions
        </a>
        <a class="item" data-tab="tab-agent-contract">
          Incoming Applications
        </a>
        <a class="item" data-tab="tab-agent-contract">
          Export to Carrier
        </a>
      </div>
    </div>

    <div class="ui hidden divider"></div>

    <div class="ui stackable grid">
      <div class="eleven wide column">
        <div class="ui hidden divider"></div>
        <div class="ui hidden divider"></div>
        <div class="ui hidden divider"></div>

        <div id="submissions" class="ui bottom attached tab segment active" data-tab="tab-detail">

          <div class="ui basic segment form">
            <div class="right floated">
              <i class="small circular yellow inverted list icon" @click="toggleShowForm"></i> New Entry &nbsp;
            </div>
          </div>
          <div class="animation-container">
            <transition name="slide-down">
              <new-form v-show="showForm" @addClient="addClient"></new-form>
            </transition>
          </div>

          <clients v-for="(client, index) in clients" :key="index" :client="client"></clients>

          <div class="ui hidden divider"></div>
        </div>
      </div>

      <notes></notes>

    </div>

  </div>

</template>

<script>
import Notes from './Notes'
import NewForm from './Form'
import Clients from './Clients'
export default {
  name: 'submissions',
  components: {
    Notes,
    NewForm,
    Clients
  },
  data() {
    return {
      showForm: false,
      clients: [
        {
          client: {
            firstName: 'John',
            lastName: 'Smith',
          },
          billingAddress: {
            street: '1600 Pennsylvania Ave',
            apt: null,
            state: 'Washington',
            county: 'DC'
          },
          billingInformation: {
            cardType: 'Master Card',
            cardNumber: '5555',
            cvc: '555',
            experationMonth: '08',
            experationYear: '2099',
          }
        }
      ]
    }
  },
  methods: {
    toggleShowForm() {
      this.showForm = !this.showForm;
    },
    addClient(client) {
      this.clients.push(client);
      this.showForm = false;
    }
  }
}
</script>

<style lang="scss">
.submission {
  margin: 1rem 0;
  .header {
    margin-top: 1rem;
  }
  .ui.vertical.segment {
    background: transparent;
    transition: 0.2s;
    margin: 0 -1rem;
    overflow: visible;
    padding: 2rem 1rem 1rem;
    &:first-of-type {
      margin-top: -0.5rem;
    }
  }
  .header.expanded {
    transform: rotate(-90deg);
    position: absolute;
    left: -5rem;
    background: white;
    padding: 1rem;
    border: 1px lightgrey solid;
    border-bottom: none;
  }
  .highlight {
    background: aliceblue;
  }
}
.history-container {
  // for .well
  overflow-x: visible;
}

.well {
  margin: 1rem -1rem;
  padding: 1rem;
}

.animation-container {
  overflow: hidden;
}

@keyframes SlideDown {
  from {
    transform: translateY(-100%);
    opacity: 0;
  }
  25% {
    transform: translateY(-85%);
  }
  50% {
    transform: translateY(-55%);
  }
  75% {
    transform: translateY(-25%);
    opacity: 0.1;
  }
  to {
    transform: translateY(0%);
    opacity: 1;
  }
}

@keyframes SlideClose {
  from {
    transform: translateY(0%);
    opacity: 1;
  }
  50% {
    transform: translateY(-50%);
  }
  75% {
    transform: translateY(-80%);
  }
  to {
    transform: translateY(-100%);
    opacity: 0;
  }
}

.slide-down {
  &-enter-active {
    animation: SlideDown 0.2s;
  }
  &-leave-active {
    animation: SlideClose 0.2s;
  }
}
</style>
