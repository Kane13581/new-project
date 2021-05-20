<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/hobbies">Hobbies</router-link>
    </div>
    <div>
      Completed todos: {{doneTodosCount}}
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import Vuex from "vuex";
// import { mapState } from "vuex";

Vue.use(Vuex);

const store = new Vuex.Store({
  state: {
    todos: [
      { id: 1, text: "...", done: true },
      { id: 2, text: "...", done: false },
    ],
  },
  getters: {
    doneTodos: (state) => {
      return state.todos.filter((todo) => todo.done);
    },
    doneTodosCount: (state, getters) => {
      return getters.doneTodos.length;
    },
    getTodoById: (state) => (id) => {
      return state.todos.find(todo => todo.id === id)
    }
  },
  count: 3,
  mutations: {
    increment(state) {
      state.count++;
    },
  },
});

export default {
  name: "App",
  store: store,
  data() {
    return {
      localCount: 4,
    };
  },
computed: {
    doneTodosCount() {
      return this.$store.getters.doneTodosCount
    },
    getTodoById() {
      return this.$store.getters.getTodoById
    },
    doneTodos() {
      return this.$store.getters.doneTodos
    },
},
};

console.log(store.getters.doneTodos);
console.log(store.getters.doneTodosCount)
console.log(store.getters.getTodoById(2));
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>

<!--computed: mapState(["count"]),-->

<!--{-->
<!--count: state => state.count,-->
<!--countAlias: 'count',-->
<!--countPlusLocalState (state) {-->
<!--return state.count + this.localCount;-->
<!--}-->
<!--}-->

// methods: { // increment() { // this.$store.commit("increment"); //
console.log(this.$store.state.count); // } // }
