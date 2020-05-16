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
          <tr v-for="postulante in postulantes">
            <td>{{ postulante.id }}</td>
            <td>{{ postulante.nombre }}</td>
            <td>{{ postulante.rut }}</td>
            <td>{{ postulante.f_nacimiento }}</td>
            <td>{{ postulante.idCarrera }}</td>
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