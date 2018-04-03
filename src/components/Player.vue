<template>
  <div class="player-wrapper">
    <div class="player">
      <iframe :src="video" />
    </div>
    <div class="description">{{description}}</div>
  </div>
</template>
<script>
export default {
  name: 'Player',
  props: ['url', 'videoDescription'],
  data () {
    return {
      video: '',
      description: ''
    }
  },
  watch: {
    url (newValue) {
      this.video = newValue
    },

    videoDescription (newValue) {
      this.description = newValue
    }
  }
}
</script>
<style>
  .player-wrapper {
    width: 68%;
  }

  .player-wrapper .player {
    height: 400px;
    border: 1px solid #ccc;
    display: flex;
    align-items: stretch;
  }

  .player-wrapper .description {
    margin-top: 30px;
    border: 1px solid #ccc;
    padding: 5px;
  }

  iframe {
    width: 100%;
  }
</style>
