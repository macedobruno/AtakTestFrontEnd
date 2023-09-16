<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Form msg="GSearch"/>
</template>

<script>
import Form from './components/SearchForm.vue'

export default {
  //name: 'App',
  name: 'SForm',
  components: {
    Form
  }
}
</script>

<style>
#search {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
