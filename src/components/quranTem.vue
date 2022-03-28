<template>
 <div id="temp">
  <p id="verse">
   {{ Verse }}
  </p>
  <p id="link">
   <a :href="link" target="_blank">{{ Chapter }}</a>
  </p>
  <n-button @click="toggle" id="shuffle">
   <i class="fa-solid fa-shuffle"></i
  ></n-button>
  <input type="checkbox" v-model="jman" />
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
    jman: false,
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
   getHadith() {
    fetch("https://api.muslim-tab.com/hadiths/english/random")
     .then((resp) => resp.json())
     .then((data) => {
      this.Verse = data.hadith
      this.Chapter = data.reference
      this.link = data.link
     })
   },
   toggle() {
    if (this.jman === true) {
     this.getHadith()
    } else {
     this.getVerse()
    }
   },
  },
  created() {
   this.getVerse()
   console.log(this.getHadith())
  },
 }
</script>

<style scoped>
 #temp {
  margin: 0 auto;
  width: 100vw;
  height: 100%;
  /* display: grid; */
  /* grid-template: 60% 30% 10%/80% 20%; */
 }
 #verse {
  margin: 0 auto;
  width: 80%;
  height: 60%;
  font-family: "Merienda", cursive;
  font-weight: 700;
  font-size: 4em;
  text-align: center;
  grid-area: verse;
  align-self: center;
  /* border: 10px solid red; */
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
 }

 #link {
  grid-area: header;
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
  grid-area: footer;
 }
 input {
  grid-area: side;
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
