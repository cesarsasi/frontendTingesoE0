<template>
  <v-container>
    <v-layout justify-center>
      <v-flex xs6>
        <h2>Lista de postulantes:</h2>
          </v-flex>
    </v-layout>

    <v-layout justify-center>
      <table>
        <tbody>
        <tr>
          <td><h2>Nombre</h2></td>
          <td><h2>Rut</h2></td>
          <td><h2>Nacimiento</h2></td>
          <td><h2>Carrera</h2></td>
        </tr>
          <tr v-for="postulante in postulantes">
            <td><v-flex class="mr-5 mt-3">{{ postulante.nombre }}</v-flex></td>
            <td><v-flex class="mr-5 mt-3">{{ postulante.rut }}</v-flex></td>
            <td><v-flex class="mr-5 mt-3">{{ postulante.f_nacimiento }}</v-flex></td>
            <td><v-flex class="mr-5 mt-3">{{ postulante.nomCarrera }}</v-flex></td>
          </tr>
        </tbody>
      </table>
    </v-layout>
  </v-container>
</template>

<script>
  import axios from 'axios'
  export default {
    name: 'ListarPostulantes',

    data: () => ({
      postulantes:null
    }),

    mounted() {
        this.getPostulantes();
    },

      methods: {
        getPostulantes(){
          axios.get('http://localhost:9898/postulantes')
            .then( response => {
              this.postulantes = response.data
            })

        .catch( e=> console.log(e))
        }
    },
  }
</script>