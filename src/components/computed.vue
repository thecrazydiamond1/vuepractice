<!-- capitalizeName() is a method: Every time the method is called (e.g., when the button is clicked), it runs again, even if the name hasn't changed.
capitalizedName is a computed property: It only recalculates when isCapitalized or name changes. If the name stays the same and the capitalization flag doesn't change, Vue won't recalculate capitalizedName. -->

<template>
    <div>
      <input v-model="name" placeholder="Enter your name" />
      <button @click="toggleCapitalize">Toggle Capitalize</button>
      <p>Computed: {{ capitalizedName }}</p>
      <p>Method: {{ capitalizeName() }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ComputedProps',
    data() {
      return {
        name: '',
        isCapitalized: false,
      };
    },
    computed: {
      capitalizedName() {
        console.log('Computed property recalculated!');
        // This will only run when 'name' or 'isCapitalized' changes
        // Derived value that depends on 'name'
        return this.isCapitalized ? this.name.toUpperCase() : this.name;
      },
    },
    methods: {
      capitalizeName() {
        console.log('Method called!');
        // This will run every time the method is called
        // Method that runs every time it's called
        return this.isCapitalized ? this.name.toUpperCase() : this.name;
      },
      toggleCapitalize() {
        // Toggle capitalization flag
        this.isCapitalized = !this.isCapitalized;
      },
    },
  };
  </script>
  