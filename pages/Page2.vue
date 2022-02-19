<template>
<div>
  <div class="navbar">
    <Navbar :link="prev"/>
    <Navbar :link="next"/>
  </div>

  <div id="page2" :class="{ green: completed }">
    <h1>Color switcher:</h1>

    <div>
      <p :class="{ green: completed }">Please make me green!</p>
      <button @click="completed = !completed">Toggle color</button>
    </div>
  </div>
</div>
</template>

<script>
import Navbar from '../components/Navbar.vue'
export default {
  name: "App",

  data(){
      return{
          completed: true,
          prev: {
            name: 'Previous',
            path: '/Page1'
          },
          next: {
            name: 'Next',
            path: '/Page3'
          }
      }
  },
  components:{
    Navbar
  },

  mounted() {
    this.completed = false;
  }
};
</script>

<style scoped>
#page2 {
  font-family: "Roboto", helvetica, arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  padding: 170px;
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

.navbar{
  display: flex;
  justify-content: space-evenly;
}
#app.green {
  background: linear-gradient(
    135deg,
    rgba(52, 73, 94, 0.9),
    rgba(65, 184, 131, 0.9)
  );
}

.green {
  color: #42b983;
}
</style>