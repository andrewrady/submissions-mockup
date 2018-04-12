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

          <!-- add contract -->
          <div class="ui basic segment form">
            <div class="right floated">
              <i class="small circular yellow inverted list icon" @click="toggleShowForm"></i> New Entry &nbsp;
            </div>
          </div>
          <div v-if="showForm">
            <new-form></new-form>
          </div>

          <div class="ui fluid styled accordion submission">
            <div class="ui title">
              <div class="ui equal width grid">
                <div class="row">
                  <div class="five wide column">
                    <span>Aetna
                      <!-- show if enrolled -->
                      <i class="olive checkmark icon"></i>
                    </span>
                    Aetna Medicare Silver Plan
                    <mark>(HMO)</mark>
                  </div>
                  <div class="column">
                    <span>Client</span>
                    Jane Hammond
                  </div>
                  <div class="two wide column">
                    <span>Effective</span>
                    4/1/2018
                  </div>
                  <div class="column">
                    <span>Status <i class="ui circular tiny empty label negative"></i></span>
                    Submitted Missing Info
                  </div>
                  <div class="column">
                    <span>Validity <i class="ui circular tiny empty label negative"></i></span>
                    Initial &amp; incomplete
                  </div>
                  <div class="one wide middle aligned column">
                    <i class="small circular inverted yellow edit icon" @click="toggleForm()"></i>
                  </div>
                </div>
                <transition name="slide-down">
                  <div v-show="showInfo" class="row highlight">
                    <div class="five wide column">
                      <span>Agent</span>
                      <a href="#">Craig James Ritter</a>
                    </div>
                    <div class="column">
                      <span>Processor</span>
                      Tim Graham
                    </div>
                    <div class="column">
                      <span>Source</span>
                      Medicareful
                    </div>
                    <div class="column">
                      <span>Signature</span>
                      2/23/2018
                    </div>
                    <div class="column">
                      <span>Keyed</span>
                      2/23/2018
                    </div>
                    <div class="two wide column states">
                      <div class="ui icon label pressed">
                        PA
                      </div>
                    </div>
                  </div>
                </transition>
                <transition name="slide-down">

                </transition>
              </div>
            </div>
          </div>

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
export default {
  name: 'HelloWorld',
  components: {
    Notes,
    NewForm
  },
  data() {
    return {
      showForm: false,
      showInfo: false,
    }
  },
  methods: {
    toggleShowInfo() {
      this.showInfo = !this.showInfo;
    },
    toggleShowForm() {
      this.showForm = !this.showForm;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.submission {
  &.accordion .content {
    display: block !important; // <-- fighting semantic
  }
  .header {
    margin-top: 1rem;
  }
  .ui.vertical.segment {
    background: transparent;
    transition: .2s;
    margin: 0 -1rem;
    overflow: visible;
    padding: 2rem 1rem 1rem;
    &:first-of-type {
      margin-top: -.5rem;
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
  // @include rgba-background-color($color-menu-bkg, .7);
}
</style>
