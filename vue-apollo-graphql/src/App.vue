<template>
  <div id="app">
    <router-link 
     class="link"
      v-for="id in $store.state.languageIds"
      :key="id"
      :to="id"
    >
      {{ $store.state.languages[id].name }}
    </router-link>

    <router-view></router-view>
  </div>
</template>

<script>
import gql from 'graphql-tag'
export default {
  name: 'app',

  async created() {
    //await this.$store.dispatch('getLanguages')
    console.log("try")
    const response = await this.$apollo.query({
      query: gql`
      query{
  findAllBooks{
    id
    isbn
  }
}`
    })
    console.log(response.data)
  console.log("try")
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

.link {
  margin: 0px 2px;
}
</style>
