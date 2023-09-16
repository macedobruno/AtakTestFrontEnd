<template>
  <div class="Search">
    <h1>GSearch</h1>
    <p>
      <!--<a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.-->
      <input type="text" v-model="input_search" placeholder="Vamos lá, pesquise o que quiser..."/>
      <input type="submit" value="Buscar" v-on:click="getSearch"/>
      <!--<label>{{ msg }}</label>-->

    </p>
    
  </div>
  <!--<div class="Results">
      <h3>{{ res }}</h3>
  </div>-->
</template>

<script>
export default {
  name: 'SForm',
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
/*input[type=text]{*/
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
  }

}
</style>
