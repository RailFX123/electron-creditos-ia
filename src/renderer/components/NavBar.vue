<template>
  <b-navbar class="is-fixed-top">
    <template slot="brand">
      <b-navbar-item tag="router-link" :to="{ path: '/' }">
        <img
          src="https://seeklogo.com/images/U/universidad-mariano-galvez-de-guatemala-logo-0B59E1DE71-seeklogo.com.png"
          alt="Lightweight UI components for Vue.js based on Bulma"
        />
        <span>&nbsp;&nbsp;Analizador de creditos con IA</span>
      </b-navbar-item>
    </template>
    <template slot="start">
      <b-navbar-dropdown label="Opciones">
        <Modal :table="true" post-title="hola bb"></Modal>
        <b-navbar-item @click="close()">
          Salir
        </b-navbar-item>
      </b-navbar-dropdown>
    </template>
  </b-navbar>
</template>

<script>
  import Modal from './Modal'
  const {remote} = require('electron')

  export default {
    name: 'navbar',
    components: { Modal },
    methods: {
      open (link) {
        this.$electron.shell.openExternal(link)
      },
      close () {
        remote.getCurrentWindow().close()
      }
    }
  }
</script>

<style></style>
