<template>
  
    <div id="index">
      <div class="content">
        <h1>Good day,</h1>

        <p>My name is <b>Dimeji Michael Ogunleye</b></p>

        <p>Please click the link below to see my solutions.</p>
      </div>

      <nuxt-link to="/Page1" class="add-btn">Solutions</nuxt-link>
    </div>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>

<style scoped>
#index {
  font-family: "Roboto", helvetica, arial, sans-serif;
  text-align: left;
  color: #2c3e50;
  padding: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  position: relative;

  background: linear-gradient(
    135deg,
    rgba(65, 184, 131, 0.9),
    rgba(52, 73, 94, 0.9)
  );

  font-size: 1.5em;
}

.content {
  width: 100%;
  padding: 2em;
  margin-top: 30px;
  position: relative;
}

@media screen and (min-width: 600px) {
  .content {
    width: 50vw;
    max-width: 15em;
  }
}

#index::before {
  content: "";
  position: absolute;
  top: -2px;
  left: 0;
  height: 2px;
  width: 100%;

  background: #35c3c1;
}

.flex-row {
  display: flex;
  margin-bottom: 1em;
}

.add-btn {
  border: none;
  font-size: 20px;
  background-color: green;
  color: #fff;
  border-radius: 4px;
  cursor: pointer;
  width: 160px;
  height: 50px;
  margin: 12px;
  transition: transform 0.3s ease-in;
  text-decoration: none;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
.add-btn:hover {
  transform: scale(1.1);
}
</style>