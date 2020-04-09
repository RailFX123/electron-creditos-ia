<template>
  <div>
    <a class="navbar-item" @click="isCardModalActive = true">
      Acerca de..
    </a>
    <b-modal :active.sync="isCardModalActive" :width="640" scroll="keep">
      <div class="card">
        <div class="card-image">
          <figure class="image is-3by3">
            <img src="imgs/logo-assets.png" alt="Image" />
          </figure>
        </div>
        <div class="card-content">
          <div class="media">
            <div class="media-left">
              <figure class="image is-64x64">
                <img
                  class="is-rounded"
                  src="https://umg.edu.gt/wp-content/uploads/2016/01/480-300x300.png"
                  alt="Image"
                />
              </figure>
            </div>
            <div class="media-content">
              <p class="title is-4">Universidad Mariano Galvez</p>
              <p class="subtitle is-6">@Grupo5- {{ postTitle }}</p>
            </div>
          </div>

          <div class="content">
            Este proyecto fue posible gracias a: <a>@bulmaio</a>. <a>#css</a>
            <a>#responsive</a>
            <br />

            <section class="section">
              <div class="container">
                <div class="columns is-centered">
                  <div class="column is-half"></div>
                </div>
                <h1 class="title">Integrantes</h1>
                <Table v-if="isTableActive" :d="data" :c="columns"></Table>
              </div>
            </section>
            <small>11:09 PM - 1 Jan 2016</small>
          </div>
        </div>
      </div>
    </b-modal>
  </div>
</template>

<script>
import Table from './Table'
export default {
  name: 'modal',
  components: { Table },
  props: {
    table: {
      type: Boolean,
      required: false
    },
    postTitle: {
      type: String,
      required: false
    }
  },
  data () {
    return {
      isImageModalActive: false,
      isCardModalActive: false,
      isTableActive: this.table,
      formProps: {
        email: 'evan@you.com',
        password: 'testing'
      },
      data: [
        {
          id: 1,
          first_name: 'Erick Fuentes',
          carnet: '0905-16-5260'
        },
        {
          id: 2,
          first_name: 'Andrea Melgar',
          carnet: '0905-16-5260'
        },
        {
          id: 3,
          first_name: 'Hector Moreira',
          carnet: '0905-16-5260'
        },
        {
          id: 4,
          first_name: 'Steven Colocho',
          carnet: '0905-16-5260'
        },
        {
          id: 5,
          first_name: 'David Natareno',
          carnet: '0905-16-5260'
        }
      ],
      columns: [
        {
          field: 'id',
          label: 'ID',
          width: '40',
          numeric: true
        },
        {
          field: 'first_name',
          label: 'Nombre'
        },
        {
          field: 'carnet',
          label: 'Carné'
        }
      ]
    }
  }
}
</script>
<style scoped>
.navbar-item img {
  max-height: 100%;
  max-width: 100%;
}
</style>
