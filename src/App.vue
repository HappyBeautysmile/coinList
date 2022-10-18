<template>
  <Home />
</template>

<script>
import Home from "@/views/Home.vue";

export default {
  name: "app",
  components: {
    Home,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#line-chart{
 /* background-color: rgb(201, 216,239) !important; */
 background: linear-gradient(180deg, rgba(238,243,249,1) 0%,  rgba(201,216,239,1) 100%)!important;
}
</style>
