<template>
<div>
  <div class="navbar">
    <Navbar :link="prev"/>
    <Navbar :link="next"/>
  </div>
  <div id="app">
    <h1>TO DO:</h1>
    <ToDo />
    <ToDo />
    <ToDo />
    <ToDo />
  </div>
</div>
</template>

<script>
import ToDo from "../components/ToDo";
import Navbar from '../components/Navbar.vue'

export default {
  name: "App",
  components: {
    ToDo,
    Navbar
  },

  data(){
    return{
      prev: {
            name: 'Previous',
            path: '/Page2'
          },
          next: {
            name: 'Next',
            path: '/'
          }
    }
  }
}
</script>

<style>
#app {
  font-family: "Roboto", helvetica, arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  padding: 25px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;

  background: linear-gradient(
    135deg,
    rgba(65, 184, 131, 0.9),
    rgba(52, 73, 94, 0.9)
  );

  font-size: 1.5em;
}
</style>