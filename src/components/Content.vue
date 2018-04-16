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
              <new-form v-show="showForm"></new-form>
            </transition>
          </div>

          <div class="ui fluid styled accordion submission">
            <div class="ui title">
              <div class="ui equal width grid">
                <div class="row">
                  <div class="four wide column">
                    John Smith
                    <i class="olive checkmark icon"></i>
                  </div>
                  <div class="two wide column">
                    <span>Date</span>
                    4/1/2018
                  </div>
                  <div class="column">
                    <span>Status
                      <i class="ui circular tiny empty label negative"></i>
                    </span><br>
                    Completed
                  </div>
                  <div class="column">
                    <span>Submiied by
                      <i class="ui circular tiny empty label positive"></i>
                    </span><br>
                    Kevin H.
                  </div>
                  <div class="one wide middle aligned column">
                    <i class="small circular inverted yellow edit icon" @click="toggleContent()"></i>
                  </div>
                </div>
              </div>
            </div>
            <div  v-show="showContent" class="ui divider"></div>
            <div class="animation-container">
              <transition name="slide-down">
                <div v-show="showContent" class="ui content">
                  <div class="ui equal width grid">
                    <div class="row">
                      <div class="five wide column">
                        <span>Address</span><br>
                        1600 Pennsylvania Ave
                      </div>
                      <div class="column">
                        <span>City</span><br>
                        Washington
                      </div>
                      <div class="column">
                        <span>State</span><br>
                        DC
                      </div>
                      <div class="column">
                        <span>zip</span><br>
                        20500
                      </div>
                    </div>
                    <div class="ui divider"></div>
                    <div class="row">
                      <div class="column">
                        <span>Card Type</span><br>
                        Master Card
                      </div>
                      <div class="column">
                        <span>Card # (last 4)</span><br>
                        4321
                      </div>
                      <div class="column">
                        <span>Experation</span><br>
                        23/2018
                      </div>
                      <div class="column">
                        <span>CVC</span><br>
                        555
                      </div>
                    </div>
                  </div>
                </div>
              </transition>
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
  name: 'submissions',
  components: {
    Notes,
    NewForm
  },
  data() {
    return {
      showForm: false,
      showContent: false,
    }
  },
  methods: {
    toggleContent() {
      this.showContent = !this.showContent;
    },
    toggleShowForm() {
      this.showForm = !this.showForm;
    }
  }
}
</script>

<style lang="scss">
.submission {
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
