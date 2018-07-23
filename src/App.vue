<template>
  <!---->
  <!--<div id="app">-->
    <!--<img src="./assets/logo.png">-->
    <!--<HelloWorld/>-->
  <!--</div>-->
  <!--<form-comp></form-comp>-->
  <router-view></router-view>
</template>

<script>
import formComp from './formComp.vue'

export default {
  name: 'App',
  components: {
    'formComp':formComp,
  }
}
</script>

<style>
#app {
  /*font-family: 'Avenir', Helvetica, Arial, sans-serif;*/
  /*-webkit-font-smoothing: antialiased;*/
  /*-moz-osx-font-smoothing: grayscale;*/
  /*text-align: center;*/
  /*color: #2c3e50;*/
  /*margin-top: 60px;*/
}
</style>
