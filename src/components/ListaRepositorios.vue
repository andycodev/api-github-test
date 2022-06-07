<template>
  <!-- <img alt="Vue logo" src="src/assets/logo.png" /> -->
  <div class="container">
    <h1>{{ data.name }}</h1>
    <span>{{ data.login }}</span>
    <h2>Mis repositorios ({{ repos.length }})</h2>
    <ul>
      <li v-for="repo in repos" :key="repo.id">
        {{ repo.name }}
        <a :href="repo.html_url" target="_blank">Ir al repositorio</a>
      </li>
    </ul>
  </div>
</template>

<script>
const API_USERS = "https://api.github.com/users/";
const API_REPOS = "https://api.github.com/users/andycodev/repos";

export default {
  data() {
    return {
      data: {},
      repos: [],
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
.container {
  background: #242424;
  color: azure;
  width: 1000px;
  margin: 0 auto;
  padding: 15px;
  border-radius: 1%;
}

h2 {
  font-size: 30px;
  text-decoration: dashed
}

ul li {
  font-family: monospace;
  font-size: 40px;
  margin: 20px;
  list-style-type: none;
}

ul li a {
  font-size: 20px;
  text-decoration: none;
  /*  display: block; */
  background: #42b883;
  color: #ffffff;
  border-radius: 2%;
  padding: 5px;
}

ul li a:hover {
  background: #ffffff;
  color: #242424;
}
</style>