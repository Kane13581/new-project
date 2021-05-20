<template>
  <div class="home">
    <h1>All destinations</h1>
    <div v-for="(destination, index) in destinations" :key="index">
      <router-link :to="`/countries/${destination.id}`">
        {{ destination.name }}
      </router-link>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import store from "./store";

export default {
  name: "Home",
  components: {},
  data() {
    return {
      destinations: store.destinations
    };
  }
};
</script>
