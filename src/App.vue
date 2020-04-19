<template>
  <div id="app">
    <img alt="moan logo" src="https://scontent.fzrh2-1.fna.fbcdn.net/v/t1.0-9/16602595_365534763821147_2942264932856879952_n.jpg?_nc_cat=105&_nc_sid=85a577&_nc_oc=AQl7PYqazHCXY9nis2ckv9GhFjA60BJwUx0B1VYugH0vGEgzSjV-4pKTvHkEdUesoHo&_nc_ht=scontent.fzrh2-1.fna&oh=88b98472d9c5291b5c6fb0f00f4fe144&oe=5EC24B8B" width="250" height= "250">
    <Moan msg="DOOR MOAN 1.0"/>
  </div>
</template>

<script>
import Moan from './components/Moan.vue'

export default {
  name: 'App',
  components: {
    Moan
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
