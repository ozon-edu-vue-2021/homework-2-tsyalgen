<template>
  <div id="app">
    <ul class="items">
      <TreeItem
          :data="root"
      ></TreeItem>
    </ul>
  </div>
</template>

<script>
import * as data from '../public/static/node_modules.json'
import TreeItem from "@/components/TreeItem";

export default {
  name: 'App',
  data() {
    return {
      root: {}
    }
  },
  components: {
    TreeItem
  },
  created() {
    this.root = data.default
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.items {
  list-style: none;
  cursor: pointer;
}
</style>
