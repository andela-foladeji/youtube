<template>
  <div>
    <SearchBar v-on:search="performSearch" />
    <div class="content">
      <Player :url="videoUrl" :videoDescription="videoDescription" />
      <Result :results="results" v-on:showVideo="show" />
    </div>
  </div>
</template>

<script>
import YTSearch from 'youtube-api-search'
import SearchBar from './SearchBar.vue'
import Player from './Player.vue'
import Result from './Result.vue'

export default {
  name: 'Home',
  components: {
    SearchBar,
    Player,
    Result
  },

  data () {
    return {
      results: [],
      videoUrl: '',
      videoDescription: ''
    }
  },

  methods: {
    performSearch (term) {
      YTSearch({key: process.env.API_KEY, term}, (videos) => {
        this.results = videos
      })
    },

    show (index) {
      this.videoUrl = `https://www.youtube.com/embed/${this.results[index].videoId}`
      this.videoDescription = this.results[index].snippet.description
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .content {
    display: flex;
    margin-top: 30px;
    justify-content: space-between;
  }
</style>
