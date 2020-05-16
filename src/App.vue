<template>
  <v-app>
    <v-app-bar
      app
      color="blue"
      dark
    >
      <div class="d-flex align-center">
        <v-btn class="mx-2" fab dark color="indigo">
          <router-link to="/">
            <v-icon dark>mdi-plus</v-icon>
          </router-link>
        </v-btn>

        <v-btn class="mx-2" fab dark color="teal">
          <router-link to="/Postulantes">
            <v-icon dark>mdi-format-list-bulleted-square</v-icon>
          </router-link>
        </v-btn>
      </div>
    </v-app-bar>

    <v-content>
      <router-view></router-view>
    </v-content>

  </v-app>
</template>



<script>
import AgregarPostulante from './components/AgregarPostulante';
import ListarPostulante from './components/ListarPostulantes';
import axios from 'axios'


export default {
  name: 'App',

  components: {
    AgregarPostulante,
    ListarPostulante,
  },

  data: () => ({
    //
  }),

  mounted(){
    console.log("mensajito para prueba")
    this.getTodos();
  },
  methods:{
    getTodos(){
      console.log("Codigo respuesta")
    }
  }
};
</script>
