<script>
import { store } from "./store"
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';

export default {
  name: "App",
  components: {
    HeaderComp,
    MainComp,
  },
  data() {
    return {
      store
    }
  },
}
</script>

<template>
  <HeaderComp />
  <MainComp />
</template>

<style>

</style>
