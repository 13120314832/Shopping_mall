<template>
  <div id="app">
    <Left/>
    <HelloWorld/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Left from './components/Left'

export default {
  name: 'app',
  components: {
    HelloWorld,
    Left
  }
}
</script>

<style>
*{
  margin: 0px;
  padding: 0px;
  border: 0px;
}
p,span,h4{
  font-size: 14px;
}
li{
    list-style-type: none;
}
input, button, select, textarea {
outline: none;
-webkit-appearance: none;
border-radius: 0;
}
body{
  width: 1400px;
  height: 100%;
  background: #000000;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 100%;
  height: 100%;
  background: red;
}
</style>
