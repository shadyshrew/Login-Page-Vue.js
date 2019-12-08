<template>
  <div id="app">
    <div v-if="authenticated == false">
      <Login @authenticated="setAuthenticated"/>
    </div>
    <div v-else>
      <Secure @authenticated="setAuthenticated"/>
    </div>
  </div>
</template>
<script>
  import Login from './components/login.vue'
  import Secure from './components/secure.vue'
  export default {
    name: 'app',
    components: {
      Login,
      Secure
    },
    data() {
      return {
        authenticated: false
      }
    },
    methods: {
        setAuthenticated(status) {
        this.authenticated = status;
      }
    }
  }
</script>
<style>
  html {
    min-height: 100%;
  }

  body {
    margin: 0;
    padding: 0;
    background-size: cover;
    background-image: url("assets/background.png");
    background-color: #696969;
    font-family: sans-serif;
    background-attachment: fixed;
    background-repeat: no-repeat;

  }


</style>
