<template>
 <h1> Welcome to Weekday Guesser!</h1>
  <div v-if="show_home">
  <BeginButtonVue @begin-clicked="begin_practice"> </BeginButtonVue>
  <button @click="begin_challenge"> Challenge </button>
  </div>
  <div v-if="show_practice">
  <PracticeComp @go-home="show_homescreen"> </PracticeComp>
  </div>
  



</template>

<script lang="ts">
import { defineComponent } from 'vue';
// import DateComp from './components/Date.vue';
import BeginButtonVue from './components/BeginButton.vue';
import PracticeComp from './components/Practice.vue';
export default defineComponent({
  name: 'App',
  components: {
    BeginButtonVue,
    // DateComp,
    PracticeComp
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
</style>
