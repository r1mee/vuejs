<template>
    <div>
        <input type="text" v-model="newTodoItem">
    </div>
  </template>
  
  <script>
  export default {
    data: function() {
      return {
        newTodoItem: ""
      }
    }
  }
  </script>