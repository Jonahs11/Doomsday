<template>

 <h1 v-if="show_home"> Welcome to Weekday Guesser!</h1>
  <div v-if="show_home">
  <BeginButtonVue @begin-clicked="begin_practice"> </BeginButtonVue>
  
  <button class="button" @click="begin_challenge"> Challenge </button>
  </div>
  <div v-if="show_practice">
  <PracticeComp @go-home="show_homescreen"> </PracticeComp>
  </div>
  <div v-if="show_challenge"> 
  <ChallengeComp @go-home="show_homescreen"> </ChallengeComp>
  </div>
  



</template>

<script lang="ts">
import { defineComponent } from 'vue';
// import DateComp from './components/Date.vue';
import BeginButtonVue from './components/BeginButton.vue';
import PracticeComp from './components/Practice.vue';
import ChallengeComp from "./components/Challenge.vue";
export default defineComponent({
  name: 'App',
  components: {
    BeginButtonVue,
    // DateComp,
    PracticeComp,
    ChallengeComp
},
  data() {
    return {
    show_home: true,
    show_practice: false,
    show_challenge: false,
    }
    
  },
  mounted() {
    console.log("This is the mounted function");
  },
  methods: {

    show_homescreen: function() {
      this.show_home = true;
      this.show_practice = false;
      this.show_challenge = false;
    },

    begin_practice: function() {
      this.show_home = false; 
      this.show_practice = true;
      console.log("toggle screens");

    },
    begin_challenge: function() {
      this.show_challenge = true;
      this.show_home = false;
    }
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.button {
    background-color: red;
    text-align: center;
    font-size: 16px;
}


</style>
