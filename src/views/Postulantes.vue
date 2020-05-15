<template>
  <div class="Postulantes">
    <ListarPostulantes msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import ListarPostulantes from '@/components/ListarPostulantes.vue'

export default {
  name: 'Postulantes',
  components: {
    ListarPostulantes
  }
}
</script>
