<template>
  <div id="app">
    <div class="ui top fixed inverted icon menu main">
      <div class="item">
        <div class="ui avatar image">
          <div class="ui large pink circular label">
            KH
          </div>
        </div>
        <div class="content">
          <div class="header">
            Hello Kevin
          </div>
        </div>
      </div>
      <div class="search item">
        <div class="ui transparent inverted icon input">
          <input type="text" placeholder="Type to search...">
          <i class="search inverted link icon"></i>
        </div>
      </div>

      <div class="right menu primary">

        <div class="ui inverted dropdown item">
          Agent
          <i class="angle down icon"></i>
          <div class="menu">
            <a class="item" href="#">
              <i class="id badge icon"></i>
              Management
            </a>
            <a class="item" href="organizations.html">
              <i class="money bill alternate outline icon"></i>
              Payments
            </a>
          </div>
        </div>
        <a class="item">
          Call Center
        </a>
        <a href="#" class="item">
          CRM
        </a>
        <a class="item" href="#">
          Flow
        </a>
        <a href="#" class="item">
          Maps
        </a>
        <a href="#" class="item">
          Submissions
        </a>
        <div class="ui inverted right dropdown item recent">
          Recent
          <i class="angle down icon"></i>
        </div>
        <a class="item" href="#">
          <img src="/images/rimdev-icon-white.svg" alt="rimdev" style="width: 2rem">
        </a>
      </div>
    </div>
    <div class="ui container app body">
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
  </div>
</template>

<script>
import Notes from './components/Notes'
import NewForm from './components/Form'
import Clients from './components/Clients'

export default {
  name: 'App',
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
@import 'assets/scss/main.scss';
</style>
