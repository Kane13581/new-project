<template>
  <section>
    <h1>
      {{destination.name}}
    </h1>
  </section>
</template>

<script>
import store from "@/store";

export default {
  name: "DestinationDetails",
  data() {
    return {
    destinationId: this.$route.params.id
    }
  },
  computed: {
    destination() {
      return store.destinations.find(
        destination => destination.id === this.destinationId
      )
    }
  }
};
</script>

<style scoped>

</style>