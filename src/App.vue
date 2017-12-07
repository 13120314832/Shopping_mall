<template>
  <div id="app">
    <Left></Left>
    <HelloWorld>
      <!-- <CfnBody></CfnBody> -->
    </HelloWorld>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Left from './components/Left'
import CfnBody from './components/CfnBody'

export default {
  name: 'app',
  components: {
    HelloWorld,
    Left,
    CfnBody,
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
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 100%;
  height: 100%;
}
</style>
