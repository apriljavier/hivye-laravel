<template>
    <div>
      <h1>Hello from Vue.js!</h1>
      <button @click="showAlert">Click Me</button>
    </div>
  </template>
  
  <script>
  export default {
    methods: {
      showAlert() {
        alert("Vue.js is working inside Laravel!");
      }
    }
  }
  </script>
  