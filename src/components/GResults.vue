<template>
  <!--<div class="Search">
    <h1>{{ msg }}</h1>
    <p>-->
      <!--For a guide and recipes on how to configure / customize this project,<br>
      check out the-->
      <!--<a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.-->
      <!--<input type="text" v-model="input_search" placeholder="Vamos lá, pesquise o que quiser...">
      <input type="submit" value="Buscar" v-on:click=getSearch(input_search)>

    </p>-->
    <!--
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank" rel="noopener">eslint</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
    -->
  <!--</div>-->

  <div class="Results">
    <h3>{{ res }}</h3>
  </div>
</template>

<script>
export default {
  name: 'SForm',
  props: {
    res: String
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
input[type=text]{
  width: 70%;
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
  min-width: auto;
  padding: 12px;
  margin-left: 0px;
  margin-right: 30px;
  border: 1px solid #2c3e50;
  /*border-radius: 4px;*/
  border-top-right-radius: 4px;
  border-bottom-right-radius: 4px;
  box-sizing: border-box;
  resize: vertical;
}
@media (max-width: 400px) {
  input[type=text]{
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
