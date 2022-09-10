<template>
  <div class="conteudo">
    <Emprestimo />
  </div>
</template>

<script>
import Emprestimo from './components/Emprestimo.vue'

export default {
  name: 'App',
  components: {
    Emprestimo
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  //text-align: center;
  color: #2c3e50;
  margin-top: 60px;

}

.conteudo {
  /* display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center; */
}
</style>
