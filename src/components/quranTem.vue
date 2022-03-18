<template>
 <div id="temp">
  <p id="verse">
   {{ Verse }}
  </p>
  <p id="link">
   <a :href="link" target="_blank">{{ Chapter }}</a>
  </p>
  <n-button @click="getVerse" id="shuffle">
   <i class="fa-solid fa-shuffle"></i
  ></n-button>
 </div>
</template>

<script>
 import { NButton } from "naive-ui"
 //  import { NAnchorLink } from "naive-ui"
 export default {
  data() {
   return {
    Verse: "",
    Chapter: "",
    link: "",
   }
  },
  components: {
   NButton,
  },
  methods: {
   getVerse() {
    fetch("https://api.muslim-tab.com/verses/english/random")
     .then((resp) => resp.json())
     .then((data) => {
      this.Verse = data.verse
      this.Chapter = data.reference
      this.link = data.link
     })
   },
  },
  created() {
   this.getVerse()
  },
 }
</script>

<style scoped>
 template {
  border: 1px green solid;
 }
 #temp {
  margin: 0 auto;
  /* border: 1px red dotted; */
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 90vh;
 }
 #verse {
  margin: 0 auto;
  width: 80%;
  font-family: "Merienda", cursive;
  font-weight: 700;
  font-size: 4em;
  text-align: center;
 }
 #link {
  margin-top: 5%;
 }
 #link a {
  text-decoration: none;
  border: 1px gray solid;
  border-radius: 10px;
  padding: 9px 20px;
  font-family: "Pangolin", cursive;
  color: #000;
  font-size: 1.1em;
 }
 #link a:hover {
  color: rgb(29, 204, 137);
  border-color: rgb(29, 204, 137);
 }
 #shuffle {
  font-size: 2em;
  padding: 0.9em;
  justify-content: center;
  margin-top: 5%;
  border-radius: 10%;
 }
 @media screen and (max-width: 400px) {
  #temp {
   width: 100vw;
  }
  #verse {
   font-size: 2em;
  }
  #link {
   margin-top: 5%;
  }
  #link a {
   font-size: 1.1em;
  }
  #shuffle {
   font-size: 1.5em;
  }
 }
</style>
