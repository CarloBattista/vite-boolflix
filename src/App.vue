<script>
import { store } from "./store"
import MainComp from "./components/MainComp.vue";

export default {
  name: "App",
  components: {
    MainComp
  },
  data() {
    return {
      store
    }
  },
}
</script>

<template>
  <MainComp />
</template>

<style>

</style>
