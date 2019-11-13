<template>
  <div id="app">
    <h1>News Display App</h1>
    <br><br>
    <div v-for="news in newsList" :key="news.id">
      <h2>{{ news.author }}</h2>
      <h2>{{ news.title }}</h2>
      <br>
      <h3 class="italic">{{ news.description }}</h3>
      <h4 class="blue">{{ news.url }}</h4>
      <h4 class="blue">{{ news.urlToImage }}</h4>
      <h3 class="green">{{ news.publishedAt }}</h3>
      <h3 class="green">{{ news.content }}</h3>
      <br>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      newsList: []
    }
  },
  mounted() {
    this.$http.get('https://newsapi.org/v2/everything?q=bitcoin&from=2019-10-13&sortBy=publishedAt&apiKey=777a399bc7fc4cdbb20d41f3812f67f4')
    .then(response => {
      this.newsList = response.data.articles
    })
  }
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.blue {
  color: blue;
}
.italic {
  font-style: italic;
}
.green {
  color: green;
}
h2 {
  text-decoration: underline;
}
</style>