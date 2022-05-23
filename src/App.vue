<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h2>Filter LearnVue Article</h2>
  <div id="app">
    <input type="text" class="input-field" placeholder="Filter Search" v-model="searchFilter" />
    <button type="button" @click="resetInput">Reset</button>
    <div class="show-result">Showing {{resultQuery.length}} results for "{{searchFilter}}"</div>
    <div class="result">
      <span class="data" v-for="r of resultQuery" :key="r.id">{{r.title}}</span>
    </div>
  </div>
</template>

<script>
  export default {
  name: "App",
  data() {
    return {
      searchFilter: null,
      resources: [
        { id: 1, title: "Introduction to Vue" },
        { id: 2, title: "DOM Interaction with Vue" },
        { id: 3, title: "Vue App Life Cycle" },
        { id: 4, title: "Vue Data, Properties, Watchers, Instances, Routing" },
        { id: 5, title: "Vue Components" },
        { id: 5, title: "Vue Forms" },
        { id: 5, title: "Vue Spas" },
        { id: 5, title: "Graph QL Integration" }
      ]
    };
  },
   methods: {
    resetInput() {
      this.searchFilter = "";
    },
  },
  computed: {
    resultQuery() {
      if (this.searchFilter) {
        return this.resources.filter(item => {
          return this.searchFilter
            .toLowerCase()
            .split(" ")
            .every(v => item.title.toLowerCase().includes(v));
        });
      } else {
        return this.resources;
      }
    }
  }
};
</script>

<style>
  body{
    margin: 0;
    padding:0;
  }
  img{
    margin-top:-14px;
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-bottom: 30px;
  }
  .input-field{
      font-size: 16px;
      width: 200px;
      padding: 10px 10px;
      border-radius: 5px;
      display: block;
      margin: 0 auto;
      margin-bottom: 20px;
  }
  .result {
      width: 500px;
      margin: 0 auto;
      margin-top: 20px;
      border: 1px solid #a0b6cd;
  }
  .result span {
      border-bottom: 1px solid #a0b6cd;
      display: block;
      padding: 15px;
      text-align: left;
  }
  .show-result {
      padding-top: 25px;
      text-align: right;
      width: 500px;
      margin: 0 auto;
  }
</style>

