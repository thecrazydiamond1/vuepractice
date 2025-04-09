<template>
    <div>
      <!-- Dynamically render each item in the list -->
      <ul>
        <li v-for="(item, index) in items" :key="index">{{ item }}</li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'NextChild',
    // Declare the 'items' prop that will be passed from the parent
    props: {
      items: {
        type: Array,
        required: true
      }
    }
  };
  </script>
  
  <style scoped>
  ul {
    list-style-type: none;
  }
  
  li {
    padding: 5px;
    background-color: lightgray;
    margin-bottom: 5px;
  }
  </style>
  



