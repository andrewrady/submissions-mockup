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
@import "assets/scss/main.scss";
</style>
