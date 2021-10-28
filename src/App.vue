<template>
  <div id="app">
   <Form />
  </div>
</template>

<script>
import Form from './components/Form.vue'

export default {
  name: 'App',
  components: {
    Form
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;700&display=swap');
#app {
  background: rgb(226, 226, 226);
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2C2738;

}
*{
  font-family: IBM Plex Sans, sans-serif;
  margin: 0;
  padding: 0;
  text-decoration: none;
}
</style>
