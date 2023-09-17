<template>
  <div class="Search">
    <h1>GSearch</h1>
    <form v-on:submit.prevent="getSearch">
      <input type="text" v-model="input_search" ref="input" placeholder="Vamos lá, pesquise o que quiser..." />
      <input type="submit" value="Buscar" v-on:click="getSearch" />
    </form>

    <span class="status">
      <h2>
        {{ status }}
      </h2>
      <hr v-if="status != ''" class="rounded">
    </span>

  </div>
  <div v-if="status != ''" class="ResultSearch">
    <div class="resultTable">
      <ul>
        <li v-for="res in resultTuple" :key="res.title">
          <span>
            <h4>{{ res.title }}</h4>
          </span>
          <p>
            <a :href="res.link" target="_blank" rel="noopener"> [{{ res.link }}] </a>
          </p>
        </li>
      </ul>
    </div>
  </div>
</template>



<script>

import axios from 'axios';

export default {
  name: 'SForm',

  data() {
    return {
      input_search: '',
      url: "http://localhost:8000/api/search?q=",
      status: '',
    }
  },

  mounted() {
    //foco no input ao carregar
    this.$refs.input.focus();
  },

  methods: {
    //metodo para consumir api de pesquisa
    getSearch() {
      this.status = 'Pesquisando...';
      try {
        axios
          //faz requisicao usando a url da api  mais valor do input
          .get(this.url + this.input_search)
          //aguarda resposta
          .then((response) => {
            //altera status 
            this.status = 'Resultados da Pesquisa';
            // converte de object para string usando padrao json
            this.results = JSON.stringify(response.data);

            // cria tupla para manter resultado da pesquisa ["title":"link"]
            this.resultTuple = [];
            JSON.parse(this.results, (tit, lin) => {

              //confima que os valores convertidos serão string
              if ((typeof lin === 'string') && (typeof tit === 'string')) {
                this.resultTuple.push({
                  title: tit,
                  link: lin
                })
              }
            });
          })
          .catch((errors) => {
            alert("ERROR: " + errors);
          })
      } catch (e) {
        alert(e);
      }
    }
  },

}
</script>

<style scoped>
h3 {
  margin-bottom: 5px;
  margin-top: 50px;
}

h2 {
  margin-bottom: 5px;
  margin-top: 30px;
}

h4 {
  margin-bottom: 7px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  width: 100%;
  /*display: inline-block;*/
  margin: 30px 0px 45px 0px;
}

a {
  color: #42b983;
}

p {
  width: 100%;
  margin-top: 0px;
  ;
}

input {
  width: 65%;
  padding: 12px;
  margin-left: 30px;
  margin-right: 0px;
  border: 1px solid #2c3e50;
  border-right-width: 0px;
  /*border-radius: 4px;*/
  border-top-left-radius: 4px;
  border-bottom-left-radius: 4px;
  box-sizing: border-box;
  resize: vertical;
}

input[type=submit] {
  width: 15%;
  /*min-width: 65px;*/
  padding: 12px;
  margin-left: 0px;
  margin-right: 30px;
  border: 1px solid #2c3e50;
  border-top-left-radius: 0px;
  border-bottom-left-radius: 0px;
  /*border-radius: 4px;*/
  border-top-right-radius: 4px;
  border-bottom-right-radius: 4px;
  box-sizing: border-box;
  resize: vertical;
  cursor: pointer;
}

h5 {
  margin-bottom: 5px;
}

hr {
  width: 80%;
  margin-bottom: 60px;
  border-top: 8px solid #e2e2e2;
  border-radius: 5px;
}

.resultTable .p {
  width: 100%;
  margin-left: 30px;
  margin-right: 30px;
  margin-bottom: 2px;
  margin-top: 10px;
}

.ResultSearch {
  word-wrap: normal;
  margin: 0 100px;
}

@media (max-width: 415px) {

  /*input[type=text]{*/
  input {
    width: 90%;
    margin-left: 5%;
    margin-right: 5%;
    border-radius: 4px;
    border-right-width: 1px;
  }

  input[type=submit] {
    width: 50%;
    margin-top: 10px;
    margin-left: 5%;
    margin-right: 5%;
    border-radius: 4px;
    border-right-width: 1px;
    cursor: pointer;
  }

}</style>
