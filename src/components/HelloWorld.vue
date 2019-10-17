<template>
  <div class="hello">
    <div>
      <h2>Ingrese el nombre del curso</h2>
      <input v-model="messageCurso" placeholder="Nombre del curso">
      <h2>Ingrese los creditos del curso</h2>
      <input v-model="messageCreditos" placeholder="Créditos">
    </div>
    <div>
      <button id="rest">REST</button>
      <button id="graphql">GRAPHQL</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Formulario de cursos'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
