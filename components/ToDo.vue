<template>
  <div class="todo">
    <input type="text" @keydown ="typedWords" v-model="message" :class="{ green: completed }" />
    <span v-if="completed" class="tick">✓</span>
    <button @click="completed = !completed" class="toggle">
      Toggle completed
    </button>

    <p class="line" v-if="!completed">To be done</p>
    <p class="line" v-else>Completed</p>
  </div>
</template>

<script>

export default {
  data(){
    return {
      message: "",
      completed: ""
    }
  },

  computed:{

    //access store variable and set completed data to false
    complete() {
      return this.completed = this.$store.state.completed
    }
},

  methods:{

    // once a key is being pressed, run a quick check on the value of message
    // if it's value length is greater than 0, set completed to true OR if the length is equal to 0 set completed back to false.
    typedWords: function() {
      if(this.message.trim().length >= 0 || this.message.trim().length === 0) {
        this.completed = !this.completed
      }
      
    }

}
};
</script>

<style scoped>
.green {
  color: #FFF;
  background-color: #42b983;
}

.toggle {
  position: absolute;
  right: -20px;
  top: 60px;
}

.tick {
  position: absolute;
  right: 0px;
  top: 20px;
  color: green;
}

.todo {
  position: relative;
  margin-top: 10px;
  width: 500px;
}

input {
  width: 100%;
  font-family: inherit;
  font-size: inherit;
  margin-top: 10px;
}

input[type="text"],
input[type="password"] {
  padding: 10px;
  border: 0;
  box-shadow: 0 0 15px 4px rgba(0, 0, 0, 0.1);
  border-radius: 5px;
}

input[type="text"]:hover,
input[type="password"]:hover {
  box-shadow: 0 0 15px 4px rgba(0, 0, 0, 0.3);
  transition: 0.3s box-shadow;
}

p.line{
  margin-bottom: 0;
}
</style>