<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/hobbies">Hobbies</router-link>
      <div>
      <button @click="add">+</button>
        {{ counter}}
        <button @click="decrease">-</button>

      </div>
    </div>
    <router-view />
  </div>
</template>

<script>
import Hobbies from "@/views/Hobbies";
import Vuex from "vuex";
import { mapState } from 'vuex';

const store = new Vuex.Store({
  state: {
    count: 5
  }
});


export default {
  name: "App",
  components: {  },
  store,
  computed: mapState({
    count: state => state.count,
    countAlias: 'count'
  }),
  comments: {
    Hobbies,
  },
  props: {

  },
  data() {
    return {
      counter: 0,
    }
  },
  methods: {
  add(){
    this.counter++
  },
  decrease(){
    this.counter--
  },

  },

}

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
