<template>
  <div id="app">
    <img src="./assets/logo.png" />
    <h1> Consumed Api For Vue Js</h1>
    <br/>
    <table class="table table-striped">
      <thead>
        <tr>
          <th scope="col">UserId</th>
          <th scope="col">Id</th>
          <th scope="col">Title</th>
          <th scope="col">Body</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="todo in todos" :key="todo.id">
          <td>{{ todo.userId }}</td>
          <td>{{ todo.id }}</td>
          <td>{{ todo.title }}</td>
          <td>{{ todo.body }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
//nos permite hacer llamadas http
import axios from "axios";
export default {
  data() {
    return {
      todos: null
    };
  },
  mounted() {
    console.log("Hola Mundo desde Mounted");
    //ejecute metodo nuevo
    this.getTodos();
  },
  methods: {
    getTodos() {
      console.log("aca va el codigo getTodos");
      axios
        .get("https://jsonplaceholder.typicode.com/posts")
        .then(response => {
          console.log(response);
          //hace que el objeto que declare en data se componga po la data
          this.todos = response.data;
        })
        .catch(e => console.log(e));
    }
  }
};
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
</style>
