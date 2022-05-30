<template>
 <h1> Welcome to Weekday Guesser!</h1>
  <DateComp/>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import HelloWorld from './components/HelloWorld.vue';
import DateComp from './components/Date.vue';

export default defineComponent({
  name: 'App',
  components: {
    DateComp
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
