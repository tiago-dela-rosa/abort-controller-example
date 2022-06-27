<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <HelloWorld />
</template>

<style>
body {
  background: #fff;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

}

section {
  width: 600px;
  display: flex;
  flex-direction: column;
  margin: 0 auto;
}

button {
  background-color: #f3f3f3;
  border: 3px solid #2FCC71;
  border-radius: 10px;
  padding: .8em 1em;
  width: 100px;
  margin-right: 5px;
  text-transform: uppercase;
  font-family: 'Montserrat', sans-serif;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.2s ease-in-out;    
}

.active {
  background-color: #2FCC71;
  color: #fff;
}

button:hover:not(.active) {
 background-color: #ddd; 
}

ul {
  list-style: none;
  padding: 0;
}

</style>
