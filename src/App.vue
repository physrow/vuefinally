<template>
  <div id="App">
    <Main/>
  </div>
</template>

<script> // in script import "namepage" from ... @Directory . Next import library for use vue-decorator
import Main from "@/components/Main";
import { Vue, Component } from 'vue-property-decorator';

// @Components { name of components
@Component({
  components: {
    Main,
  }
})
export default class App extends Vue {} // default
</script>
<style>
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 600px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>