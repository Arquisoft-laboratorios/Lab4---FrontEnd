<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>
    <div>
      <h2>Ingrese el nombre del curso</h2>
      <input type="text" v-model="name" placeholder="Ingrese el nombre del curso"/>
      <h2>Ingrese los creditos del curso</h2>
      <input type="text" v-model="credits" placeholder="Creditos"/>
    </div>
    <div>
      <input type="button" @click="createPost()" value="REST">
      <!--
      <ul v-if="posts && posts.length">
        <li v-for="post of posts" v-bind:key="post.id">
          <p><strong>{{post.name}}</strong></p>
          <p>{{post.credits}}</p>
        </li>
      </ul>
      -->
      <button id="graphql">GRAPHQL</button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      name: null,
      credits: null,
      posts: []
    }
  },
  created () {
    this.$http.get('').then((response) => {
      this.posts = response.data
    })
      .catch((e) => {
        console.error(e)
      })
  },
  methods: {
    createPost () {
      this.$http.post('', {
        name: this.name,
        credits: this.credits
      }).then((response) => {})
        .catch((e) => {
          console.error(e)
        })
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
