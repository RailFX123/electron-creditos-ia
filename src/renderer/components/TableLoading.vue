<template>
  <section>
    <div class="card mtest">
      <section class="hero">
        <div class="hero-body">
          <div class="container  has-text-centered">
            <h1 class="title">
              Creditos guardados
            </h1>
          </div>
          <section >
            <b-table
              :data="isEmpty ? [] : movies"
              :columns="col"
              :paginated="isPaginated"
              :bordered="isBordered"
              :striped="isStriped"
              :narrowed="isNarrowed"
              :hoverable="isHoverable"
              :loading="isLoading"
              :focusable="isFocusable"
              :mobile-cards="hasMobileCards"
            >
              <template slot="empty">
                <section class="section">
                  <div class="content has-text-grey has-text-centered">
                    <p>
                      <b-icon icon="emoticon-sad" size="is-large"></b-icon>
                    </p>
                    <p>No tienes creditos agregadas :C</p>
                  </div>
                </section>
              </template>
            </b-table>
          </section>
        </div>
      </section>
    </div>
  </section>
</template>

<script>
export default {
  data () {
    return {
      movies: [],
      isLoading: true,
      countUpdatingTable: [],
      isEmpty: false,
      isBordered: false,
      isStriped: false,
      isNarrowed: false,
      isHoverable: false,
      isFocusable: false,
      isPaginated: true,
      hasMobileCards: true,
      col: [
        {
          field: 'Nombre',
          label: 'Nombre'
        },
        {
          field: 'Trabaja',
          label: 'Trabaja'
        },
        {
          field: 'Salario',
          label: 'Salario'
        },
        {
          field: 'Aprobado',
          label: 'Aprobado'
        }
      ]
    }
  },
  async created () {
    try {
      let filePath = 'myfile.txt'
      const fs = require('fs')
      if (fs.existsSync(filePath)) {
        fs.readFile(filePath, 'utf-8', (err, d) => {
          if (err) {
            this.notification(
              'Ha ocurrido un error actualizando el archivo',
              'is-danger',
              1000
            )
          } else {
            let jarray = JSON.parse(d)
            this.movies = jarray
            this.isLoading = false
          }
        })
      } else {
        this.isLoading = false
      }
    } catch (e) {
      this.isLoading = false
    }
  }
}
</script>
<style scoped>
.mtest{
  height: 100%;
}
</style>
