<template>
  <b-navbar>
    <template slot="brand">
      <b-navbar-item tag="router-link" :to="{ path: '/' }">
        <img
          src="https://seeklogo.com/images/U/universidad-mariano-galvez-de-guatemala-logo-0B59E1DE71-seeklogo.com.png"
          alt="Lightweight UI components for Vue.js based on Bulma"
        />
        <span>   Analizador de creditos con IA</span>
      </b-navbar-item>
      
    </template>

    <template slot="end">
      <b-navbar-item tag="div">
        <div class="buttons">
          <a class="button is-dark">
              Salir
          </a>
        </div>
      </b-navbar-item>
    </template>
  </b-navbar>
</template>

<script></script>

<style></style>
