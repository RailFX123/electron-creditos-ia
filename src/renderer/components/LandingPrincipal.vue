<template>
<div>
    <NavBar></NavBar>
    <Body></Body>
</div>
</template>

<script>
  import NavBar from './NavBar'
  import Body from './LandingPage'
  import Menu from './Menu'

  export default {
    name: 'landing-page',
    components: { NavBar, Body, Menu },
    methods: {
      open (link) {
        this.$electron.shell.openExternal(link)
      }
    }
  }
</script>

<style>
</style>