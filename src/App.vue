<template>
  <router-view />
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
body {
  margin: 0;
  padding: 0;
}
.logo {
  width: 100px;
}

.register input, .login input, .add input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin: 0 auto;
  margin-bottom: 30px;
  border: 1px solid skyblue;
}

.register button, .login button, .add button {
  width: 300px;
  height: 40px;
  border: 1px solid skyblue;
  background: skyblue;
  color: #fff;
  cursor: pointer;
}
</style>
