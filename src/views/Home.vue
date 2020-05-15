<template>
  <div class="home">
    <AgregarPostulantes msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import AgregarPostulantes from '@/components/AgregarPostulante.vue'

export default {
  name: 'Home',
  components: {
    AgregarPostulantes
  }
}
</script>
