<template>
  <div class="Search">
    <h1>GSearch</h1>
      <!--<a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.-->
    <form>
      <input type="text" v-model="input_search" ref="input" placeholder="Vamos lá, pesquise o que quiser..."/>
      <input type="submit" value="Buscar" v-on:click="getSearch"/>
    </form>

    <span class="status">
      <h3>
        {{status}}
      </h3>
    </span>

  </div>
  <template v-if="status != ''">
    <div class="ResultSearch">
      <!--<span> {{ results }}</span>-->
      <div class="resultTable">
        <ul>
          <li v-for="res in resultTuple" :key="res.title">
            <p>
              <span><h4>{{ res.title }}</h4></span>
              <br>
              <a :href="res.link" target="_blank" rel="noopener"> [{{ res.link }}] </a>
            </p>
          </li>
        </ul>
      </div>
    </div>
  </template>

</template>



<script>

// eslint-disable-next-line no-unused-vars
import axios from 'axios';

export default {
  name: 'SForm',
  //result:'',
  //results:'',
  data(){
    return {
      input_search:'',
      url:"http://localhost:8000/api/search?q=",
      //results: [],
      status:'',
    }
  },

  mounted(){
    this.$refs.input.focus();
  },

  methods:{
    getSearch(e){
      e.preventDefault(e);
      /*if (!this.input_search){
        alert("está vazio? pelo menos entrou aqui");
        this.status='';
      }
      */
      this.status='Pesquisando...';
      //alert("chegou aqui");
      //alert(this.url+this.input_search);

      try{
        axios
          .get(this.url+this.input_search)
          .then((response) => {
            this.status='Resultados da Pesquisa';
            //alert(response);
            this.results = JSON.stringify(response.data);
            
            //alert('response: '+typeof(this.results));
            //alert('response data: '+typeof(response.data));
            
            //alert('value: '+response.value);
            //alert('data value: '+response.data.value);
            
            //alert('results type: '+typeof(this.results));
            //let titles=[];
            //let links=[];
            this.resultTuple = [];
            JSON.parse(this.results, (tit, lin) => {
              //alert("titles: "+tit);
              //alert("links: "+lin);
              this.resultTuple.push({
                title: tit,
                link: "http://"+lin+"/"
              })
              //titles.push(title);
              //links.push(link);
            });


            //alert('parse results: '+typeof(JSON.parse(this.results)));
            //alert('parse: '+JSON.parse(this.results));
            //alert('parse key: '+JSON.parse(this.results));
            //alert('type parsed: '+parsed);
            //alert('parsed: '+parsed);
            //let respDataStr = response.data //texto
            //let jsObject = JSON.parse(respDataStr) //converte texto recebido para
            //this.windows = jsObject
            //this.jsresults = JSON.parse(respDataStr);

            //alert(this.results);
            
          })
          .catch((errors) => {
            alert("ERROR: "+errors);
          })
        /*this.parcialr=[];
        for (this.parcialr in this.response.data){
          alert (this.parcialr);
        }*/
      } catch(e){
        alert(e);
      }
    }
  },
  
  props: {
    title: String,
    res: String,
    search: String,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
p{
  width: 100%;
}
input{
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
input[type=submit]{
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
.resultTable .h4 .p{
  width: 100%;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 2px;
}
.ResultSearch{
  word-wrap: normal;
}
@media (max-width: 415px) {
  /*input[type=text]{*/
  input{
    width: 90%;
    margin-left: 5%;
    margin-right: 5%;
    border-radius: 4px;
    border-right-width: 1px;
  }
  input[type=submit]{
    width: 50%;
    margin-top: 10px;
    margin-left: 5%;
    margin-right: 5%;
    border-radius: 4px;
    border-right-width: 1px;
    cursor: pointer;
  }

}
</style>
