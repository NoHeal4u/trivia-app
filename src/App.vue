<template>
  <div id="app">
    <nav-bar />
    <router-view></router-view>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue'

export default {
  name: 'app',
  components: {

    NavBar

  }
}
</script>

<style>

</style>
