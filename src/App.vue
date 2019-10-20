<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>
    <div>
      <h2>Ingrese el nombre del curso</h2>
      <input type="text" v-model="name" placeholder="Nombre del curso"/>
      <h2>Ingrese los creditos del curso</h2>
      <input type="text" v-model="credits" placeholder="Creditos"/>
    </div>
    <div>
      <input type="button" @click="createCourseRest(name, credits)" value="REST">
      <input type="button" @click="createCourse(name, credits)" value="GraphQL">
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag'
import axios from 'axios'

export default {
  data () {
    return {
      course: {
        name: null,
        credits: null
      }
    }
  },
  name: 'app',
  apollo: {
    allCourses: gql`query {
      allCourses {
        name,
        credits
      }
    }`
  },
  methods: {
    createCourse (name, credits) {
      this.$apollo.mutate({
        mutation: gql`mutation ($name: String!, $credits: Int!) {
          createCourse(course: {name: $name, credits: $credits}) {
            name
            credits
          }
        }`,
        variables: {
          name: name,
          credits: credits
        }
      })
      alert('Course created successfully (from GraphQL) -> name: ' + name + ', credits: ' + credits)
    },
    createCourseRest (name, credits) {
      axios({
        method: 'post',
        url: 'http://3.130.145.129:3000/courses-ms/resources/courses',
        data: {
          name: name,
          credits: credits
        }
      })
      alert('Course created successfully (from Microservice) -> name: ' + name + ', credits: ' + credits)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
