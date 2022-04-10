<template>
  <div id="app">
    <NoMeDecido/>
  </div>
</template>

<script>
import NoMeDecido from './components/NoMeDecido.vue'

export default {
  name: 'App',
  components: {
    NoMeDecido
  }
}
</script>

<style>
#app {  
  font-family: 'helvetica', Times, serif;
  color: white;
  text-align: center;
  display: flex;
  justify-content: center;
  }
body{
  background-color: black;
}
</style>
