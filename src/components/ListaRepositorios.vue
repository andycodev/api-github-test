<template>

  <!-- <img alt="Vue logo" src="src/assets/logo.png" /> -->

  <h1>{{data.name}}</h1>
  <span>{{data.login}}</span>
  <h2>Mis repositorios</h2>
  <ul>
    <li v-for="repo in repos" :key="repo.id">
      {{repo.name}}
      <a :href="repo.html_url" target="_blank">Ir al repositorio</a>
    </li>
  </ul>

</template>

<script>
const API_USERS = "https://api.github.com/users/";
const API_REPOS = "https://api.github.com/users/andycodev/repos";

export default {
  data() {
    return {
      msg: "holaaaaa",
      data: {},
      repos: []
    };
  },
  mounted() {
    this.getInfo();
    this.getRepos();
  },
  methods: {
    async getInfo() {
      const response = await fetch(API_USERS + "andycodev");
      this.data = await response.json();
      console.log(this.data);
    },

    async getRepos() {
      const response = await fetch(API_REPOS);
      this.repos = await response.json();
      console.log(this.repos);
    },
  },
};
</script>

<style scoped>

img {
  margin-left: 30px;
}

ul li {
  font-family: monospace;
  font-size: 40px;
  margin: 20px;
  list-style-type: none;
  
}

ul li a {
 font-size: 10px;
 text-decoration: none;
}

</style>