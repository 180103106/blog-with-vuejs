<template>
  <div id="app">
    <button>
      <router-link to = "/posts">HomePage</router-link>
    </button>
    <button>
      <router-link to = "/posts-create">AddNewBlog</router-link>
    </button>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir',sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  margin-top: 60px;
}
</style>
