<template>
 <h1> Welcome to Weekday Guesser!</h1>
  <div v-if="show_begin_button">
  <BeginButtonVue @begin-clicked="toggle_begin"> </BeginButtonVue>
  </div>
  
  <DateComp/>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import HelloWorld from './components/HelloWorld.vue';
import DateComp from './components/Date.vue';
import BeginButtonVue from './components/BeginButton.vue';

export default defineComponent({
  name: 'App',
  components: {
    BeginButtonVue,
    DateComp
  },
  data() {
    return {
    show_begin_button: true
    }
    
  },
  methods: {
    toggle_begin: function() {
      this.show_begin_button = !this.show_begin_button;
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
