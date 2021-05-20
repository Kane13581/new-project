<template>
  <div class="home">
    <div v-for="destination in destinations" :key="destination.name">
      <router-link :to="destination.slug">
      <h2>{{destination.slug}}</h2>
      </router-link>
    </div>
    <figure>
      <router-link :to="destination.name">
        `${destination.name}`
      </router-link>
    </figure>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: "home",
  components: {

  },
  data() {
    return {

    }
  }
};
</script>
