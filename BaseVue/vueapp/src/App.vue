<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js Đại ca Dương1"/>
    {{dulieu.temperatureC + " " + dulieu.summary}}
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'
export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data()
  {
    return {
        dulieu: ""
    }
  },
  beforeCreate()
  {
    let self = this;
    axios.get('/api/WeatherForecast/ThoiTiet')
    .then(res => {
       self.dulieu = {...res.data[0]}
       console.log(self.dulieu);
    }).catch(er =>
    {
      console.log(er);
    })
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
</style>
