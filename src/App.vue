<template>
  <div id="app">
    <h1>
      {{msg}}
    </h1>
    {{status}}
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'app',
  data () {
    return {
      msg: 'Vue-Axios',
      status: ''
    }
  },
  created () {
    this.loadQuote();
  },
  methods: {
    loadQuote () {
      this.status = 'loading..!';
      // axios getReq
      var self = this;
      // axios.get(`http://jsonplaceholder.typicode.com/posts`)
      axios.get('http://ron-swanson-quotes.herokuapp.com/v2/quotes')
      .then(function(response) {
        console.log(response);
        self.status = response.data[0];
      })
      .catch(function(error){
        self.status = 'Something nesty happened...!' + error;
      });
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 20px;
}

h1, h2 {
  font-weight: normal;
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
</style>
