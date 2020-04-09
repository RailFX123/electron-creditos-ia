<template>
  <section>
    <div class="card">
      <section class="hero">
        <div class="hero-body">
          <div class="container  has-text-centered">
            <h1 class="title">
              Calculadora
            </h1>
          </div>
          <section>
            <b-field label="Nombre">
              <b-input
                minlength="10"
                maxlength="50"
                v-model="name"
                placeholder="Juanito Perez"
                required
              ></b-input>
            </b-field>
            <b-field label="Labora actualmente?">
              <div class="block">
                <b-radio
                  v-model="radio"
                  name="name-si"
                  native-value="Si"
                  required
                >
                  Si
                </b-radio>
                <b-radio
                  v-model="radio"
                  name="name-no"
                  native-value="No"
                  required
                >
                  No
                </b-radio>
              </div>
            </b-field>
            <b-field label="Ingreso Mensual">
              <div class="block">
                <b-radio
                  v-model="radio2"
                  name="name-meny1500"
                  native-value="Menores a 1500"
                  required
                >
                  Menores a 1500
                </b-radio>
                <b-radio
                  v-model="radio2"
                  name="name-ig1500"
                  native-value="Iguales a 1500"
                  required
                >
                  Iguales a 1500
                </b-radio>
                <b-radio
                  v-model="radio2"
                  name="name-may1500"
                  native-value="Mayores a 1500"
                  required
                >
                  Mayores a 1500
                </b-radio>
              </div>
            </b-field>
            <section>
              <b-button class="button is-primary" @click="saveFile"
                >Guardar</b-button
              >
            </section>
          </section>
          <!-- <p class="content">
            <b>Nombre:</b>
            {{ name }}
          </p>
          <p class="content">
            <b>Labora:</b>
            {{ radio }}
          </p>
          <p class="content">
            <b>Labora:</b>
            {{ radio2 }}
          </p> -->
        </div>
      </section>
    </div>
  </section>
</template>

<script>
export default {
  data () {
    return {
      name: '',
      radio: '',
      radio2: ''
    }
  },
  methods: {
    saveFile () {
      if (!this.name || !this.radio || !this.radio2) {
        this.notification('Rellena todos los campos', 'is-danger', 1000)
      } else {
        var data = {
          Nombre: this.name,
          Trabaja: this.radio,
          Salario: this.radio2
        }
        var array = []
        console.log(this.radio)
        if (this.radio2 === 'Mayores a 1500') {
          data['Aprobado'] = 'Si'
        } else {
          data['Aprobado'] = 'No'
        }
        array.push(data)
        let filePath = 'myfile.txt'
        try {
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
                console.log(jarray)
                jarray.push(data)
                console.log(jarray)
                fs.writeFileSync(filePath, JSON.stringify(jarray), 'utf-8')
                this.notification(
                  'Se ha añadido un nuevo credito :D',
                  'is-success',
                  1000
                )
                this.name = ''
                this.radio = ''
                this.radio2 = ''
              }
            })
          } else {
            fs.writeFileSync(filePath, JSON.stringify(array), 'utf-8')
            this.notification(
              'Archivo guardado con exito :D',
              'is-success',
              1000
            )
            this.name = ''
            this.radio = ''
            this.radio2 = ''
          }
        } catch (e) {
          console.log(e)
          this.notification(
            'Ha ocurrido un error grave: ' + e,
            'is-danger',
            5000
          )
        }
      }
    },
    notification (mensaje, tipo, tiempo) {
      this.$buefy.notification.open({
        duration: tiempo,
        message: mensaje,
        position: 'is-top-right',
        type: tipo
      })
    }
  }
}
</script>
