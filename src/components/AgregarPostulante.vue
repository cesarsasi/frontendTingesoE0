<template>
  <v-container>
    <v-layout justify-center>
      <v-flex xs6>
        <h2>Ingrese los datos del postulante:</h2>
      </v-flex>

    </v-layout>

    <v-layout justify-center>
      <v-flex class="mt-3" xs6>
        <v-form
                ref="form"
                v-model="valid"
                lazy-validation
        >
          <v-text-field
                  v-model="name"
                  :rules="nameRules"
                  label="Nombre"
                  required
          ></v-text-field>

          <v-text-field
                  v-model="rut"
                  :counter="10"
                  :rules="rutRules"
                  label="Rut"
                  required
          ></v-text-field>

          <v-text-field
                  v-model="birth"
                  :rules="birthRules"
                  label="Fecha de Nacimiento (AAAA/MM/DD)"
                  required
          ></v-text-field>

          <v-select
                  v-model="select"
                  :items="carreras"
                  item-text="id"
                  :rules="[v => !!v || 'Campo requerido']"
                  label="Carrera"
                  required
          ></v-select>

          <v-btn
                  color="error"
                  class="mr-4"
                  @click="reset"
          >
            Reiniciar formulario
          </v-btn>

          <v-btn
                  :disabled="!valid"
                  color="success"
                  class="mr-4"
                  @click="validate"
          >
            Enviar
          </v-btn>

        </v-form>
      </v-flex>
    </v-layout>

  </v-container>
</template>




<script>
  import axios from "axios";

  export default {
    name: 'AgregarPostulante',

    data: () => ({
      test: true,

      valid: true,
      name: '',
      nameRules: [
        v => !!v || 'Campo requerido',
        v => (v && v.length <= 100) || 'Excede el maximo de caracteres',
      ],
      rut: '',
      rutRules: [
        v => !!v || 'Campo requerido',
        v => (v && v.length <= 10) || 'Rut incorrecto',
      ],
      birth: '',
      birthRules: [
        v => !!v || 'Campo requerido',
        v => (v && v.length <= 10) || 'Formato incorrecto',
      ],
      select: null,
      carreras: null,
    }),

    mounted() {
      this.getCarreras();
    },

    methods: {
      validate () {
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },

      getCarreras() {
        axios.get('http://localhost:9898/carrera') //Reemplazar url
                .then( response => {
                  this.carreras = response.data
                })

                .catch( e=> console.log(e))
      }
    },
  }
</script>