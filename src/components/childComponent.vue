<template>
    <div>
      <p>{{ message }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ChildComponent',
    props: ['message']
  };
  </script>
  
  <style scoped>
  p {
    color: blue;
  }
  </style>
  