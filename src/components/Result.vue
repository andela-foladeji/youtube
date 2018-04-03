<template>
  <div class="result-list">
    <div v-for="(eachResult, index) in allResults" :key="index" v-on:click="play(index)" >
      <img :src="eachResult.snippet.thumbnails.default.url" :alt="eachResult.snippet.title" :title="eachResult.snippet.title" />
      <p>{{eachResult.snippet.title}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Result',
  props: ['results'],
  data () {
    return {
      allResults: []
    }
  },
  methods: {
    play (index) {
      this.$emit('showVideo', index)
    }
  },
  watch: {
    results (value) {
      this.allResults = value
    }
  }
}
</script>

<style>
  .result-list {
    width: 30%;
    border: 1px solid #ccc;
    padding: 10px 2%;
  }

  .result-list > div {
    display: flex;
  }

  .result-list > div p {
    font-size: 12px;
  }
</style>
