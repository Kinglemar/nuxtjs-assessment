<template>
<div>
  <div class="navbar">
    <Navbar :link="prev"/>
    <Navbar :link="next"/>
  </div>
  <div id="page3">
    <h1>TO DO:</h1>
    <ToDo />
    <ToDo />
    <ToDo />
    <ToDo />
  </div>
</div>
</template>

<script>
import ToDo from "../components/ToDo.vue";
import Navbar from "../components/Navbar.vue";

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
#page3 {
  font-family: "Roboto", helvetica, arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  padding: 10px;
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
h1{
  margin: 5px
}
#page3.p{
  font-size: 1rem;
}

.navbar{
  display: flex;
  justify-content: space-evenly;
}
</style>