<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/hobbies">Hobbies</router-link> |
      <router-link to="/brazil">Brazil</router-link> |
      <router-link to="/jamaica">Jamaica</router-link> |
      <router-link to="/hawaii">Hawaii</router-link> |
      <router-link to="/panama">Panama</router-link>
    </div>
    <router-view />
    <div>
      {{ count }}
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import Vuex from "vuex";
import { mapState } from "vuex";

Vue.use(Vuex);

const store = new Vuex.Store({
  state: {
    count: 3,
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
      return state.todos.find((todo) => todo.id === id);
    },
  },
  mutations: {
    increment(state) {
      state.count++;
    },
    incrementBy (state, payload) {
      state.count += payload.amount;
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
  computed: mapState([
   'count'
  ]),
};

store.commit("incrementBy", {amount: 30});
console.log(store.state.count);

//
// console.log(store.getters.doneTodos);
// console.log(store.getters.doneTodosCount)
// console.log(store.getters.getTodoById(2));
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


<!--count: (state) => state.count,-->
<!--countAlias: "count",-->
<!--countPlusLocalState(state) {-->
<!--return state.count + this.localCount;-->
<!--},-->

<!--{-->
<!--doneTodosCount() {-->
<!--return this.$store.getters.doneTodosCount-->
<!--},-->
<!--getTodoById() {-->
<!--return this.$store.getters.getTodoById-->
<!--},-->
<!--doneTodos() {-->
<!--return this.$store.getters.doneTodos-->
<!--},-->
<!--},-->

// methods: { // increment() { // this.$store.commit("increment"); //
console.log(this.$store.state.count); // } // }
