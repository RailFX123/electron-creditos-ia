<template>
  <div>
    <NavBar></NavBar>
    <Hero></Hero>
    <br>
    <div class="columns m1-lr">
      <div class="column is-half">
        <FormCredito></FormCredito>
      </div>
      <div class="column is-half">
        <TablaPro></TablaPro>
      </div>
    </div>
  </div>
</template>

<script>
import NavBar from './NavBar'
import Menu from './Menu'
import FormCredito from './FormCredito'
import Hero from './Hero'
import TablaPro from './TableLoading'

export default {
  name: 'landing-page',
  components: { NavBar, FormCredito, Menu, TablaPro, Hero },
  data () {
    return {
      data: this.d,
      columns: this.c
    }
  },
  methods: {
    open (link) {
      this.$electron.shell.openExternal(link)
    }
  }
}
</script>

<style scoped>
.m1-lr{
  padding-left: 1.5%;
}

</style>
