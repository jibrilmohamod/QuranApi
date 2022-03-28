<template>
 <quranTem> </quranTem>
</template>

<script>
 import quranTem from "./components/quranTem.vue"

 export default {
  name: "App",
  components: {
   quranTem,
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
  /* margin-top: 4em; */
  display: grid;
  margin-top: 6em;
  height: 90vh;
 }
</style>
