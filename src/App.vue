<template>
  <SignUp></SignUp>
</template>

<script>
import SignUp from './components/SignUp.vue'

export default {
  name: 'App',
  components: {
    SignUp
  }
}
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
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background: #e9e9e9;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
