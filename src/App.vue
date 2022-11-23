<script setup>
  import VideoPlayer from './components/VideoPlayer.vue'
  import VideoDetails from './components/VideoDetails.vue'
  import VideoComments from './components/VideoComments.vue'

</script>

<template>
  <div class="app">
    <VideoPlayer class="item1"/>
    <VideoDetails class="item2" />
    <VideoComments class="item3"/>
  </div>
</template>

<style scoped>
  .item1 { grid-area: header; }
  .item2 { grid-area: main; }
  .item3 { grid-area: footer; }
  .app {
    display: grid;
     grid-template-areas:
      'header header header main main'
      'header header header footer footer'
      'header header header footer footer'
      'header header header footer footer'
      'header header header footer footer'
      'header header header footer footer'
      'header header header footer footer'
      'header header header footer footer';
    gap: 10px;
    padding: 10px;
  }
</style>
