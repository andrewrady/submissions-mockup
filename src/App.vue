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
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style lang="scss">
form {
  padding: 2%;
}
.dimmer {
  animation: fadeIn 0.2s;
  background: rgba(black, 0.8);
  height: 100%;
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 10;
}
.positioning {
  display: flex;
  align-item: flex-start;
  justify-content: center;
  width: 100%;
  height: 30vh;
  left: 0;
  top: 0;
  z-index: 30;
}
.parent {
  width: 97% !important;
  position: fixed;
  top: 30vh;
  z-index: 30;
}
select.focused {
  &:focus {
    color: grey;
    font-size: 10vh !important;
    // height: 280px;
    // transform: scale(1.1);
    @extend .positioning;
    width: 100% !important;
    // margin: inherit -1em;
  }
}
input.focused {
  transition: 0.2s;
  &:focus {
    font-size: 20vh !important;
    padding: 5%;
    @extend .positioning;
  }
}

label.focused {
  color: white;
  font-size: 10vh;
  z-index: 30;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}

.fadeIn {
  animation-name: fadeIn;
}
</style>
