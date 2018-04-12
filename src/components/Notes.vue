<template>
  <div class="five wide column notes">
    <!-- notes menu -->
    <div class="ui text menu">
      <a class="active item">
        <i class="small circular inverted yellow add icon"></i>
        Submission note
      </a>
      <div class="right menu">
        <div class="ui right floated note-stat">
          <i class="small lightgrey sticky note icon"></i>
          1
        </div>
      </div>
    </div>
    <div class="ui note fluid card edit">
      <div class="content">
        <div class="meta">
          <p><img class="ui avatar mini image" src="https://avatars2.githubusercontent.com/u/6231956?v=3&s=460">Kevin Hougasian
            <i class="small yellow calendar outline icon"></i> Feb 2, 2016</p>
        </div>

        Note for current submmission.
      </div>
      <div class="ui note-footer grid">
        <div class="eleven wide column tags footer-column">
          <div class="footer-menu">
            <i class="yellow vertical ellipsis icon"></i>
          </div>
          <div class="ui tiny labels footer-tags">
            <div class="ui basic yellow circular label icon">
              Public
              <i class="yellow close icon"></i>
            </div>
          </div>
        </div>
        <div class="five wide right aligned column actions">
          <i class="red trash icon"></i>
          <i class="yellow write square icon"></i>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'notes'
}
</script>

<style>

</style>
