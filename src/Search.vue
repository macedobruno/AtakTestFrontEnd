<template>
  <img class="logo" alt="GSearch logo" src="./assets/logo.png">
  <Form/>
</template>

<script>
  import Form from './components/SearchForm.vue'

  export default {

    data(){
      return {
      };
    },

    name: 'SForm',
    components: {
      Form,
    },
  };

  
</script>

<style>
.logo{
  width: 256px;
}
@media (max-width: 415px) {
  .logo{
    width: 65%;
  }
}

#search {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#results {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
