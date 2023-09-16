<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <!--<Form title="GSearch" res="Escreva alguma coisa"/>-->
  <Form/>
  <GResults res="Escreva alguma coisa"/>
</template>

<script>
  import Form from './components/SearchForm.vue'
  import GResults from './components/GResults.vue'
  //import axios from "axios";

  export default {

    data(){
      return {
        results: {},
        input_search:"",
        info:null,
        loading:true,
        errored:false,
        url:"localhost:8000/api/search?q="
      };
    },

    //name: 'App',
    name: 'SForm',
    components: {
      Form,
      GResults
    },

    methods: {
      getSearch: function(){
        alert("Caiu aqui");
        console.log("Caiu aqui");
        this.input_search="Pipoca";
        this.res = this.input_search;
        //input_search="Caiu Aqui";
        
        /*
        console.log("Caiu aqui");
      //getSearch: function (input) {
        //input.preventDefault();

        axios
          .get(this.url+inputsearch)
          .then((res) => {
            this.results = res.data;
          })
          .catch((error) => {
            console.log(error);
          })
        */
        /*
        
        try{
          const response = await this.$http.get(
            "localhost:8000/api/search?q=pipoca"
          );
          this.results = response.data;
          console.log(results);
        } catch(error){
          console.log(error);
        }
        */
      }
    },
  };

  
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

#results {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
