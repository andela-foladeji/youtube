<template>
  <div>
    <form class="search-form" v-on:submit.prevent="searchVideos">
      <input type="text" v-model="searchTerm" placeholder="Search..." />
    </form>
  </div>
</template>
<script>
export default {
  name: 'SearchBar',

  data () {
    return {
      searchTerm: ''
    }
  },

  methods: {
    searchVideos () {
      this.$emit('search', this.searchTerm)
    }
  }
}
</script>

<style>
  .search-form {
    width: 80%;
    margin: auto;
  }
  .search-form input {
    width: 100%;
    height: 35px;
    border: 1px solid #ccc;
    outline: none;
    padding: 0 5px;
  }
  .search-form input:focus {
    outline: none;
  }
</style>
