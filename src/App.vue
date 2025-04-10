
<template>
  <div>
    <!-- v-bind -->
    <h1 v-bind:class="{active: isActive}">{{ message }}</h1>
    <p>{{ count }}</p>
    <!-- v-model -->
    <input type="text" v-model="count" />
    <!-- v-bind -->
    <input type="text" v-bind:value="count" @input="count = $event.target.value" />
    <!-- v-if -->
    <p v-if="role==='admin'">This is admin</p>
    <p v-else-if="role==='user'">This is user</p>
    <p v-else>Access Denied!</p>
    <!-- v-show -->
    <button @click="isVisible = !isVisible">Toggle Message</button>
    <p v-show="isVisible">Now you see me!</p>
    <!-- v-for -->
    <ul>
    <li v-for="(todo, index) in todos" :key="index">
      {{ index + 1 }}. {{ todo }}
    </li>
  </ul>
  <!-- v-text -->
  <p v-text="message"></p>
  <!-- v-html -->
  <div v-html="htmlContent"></div>
  <!-- methods in vue component -->
  <HelloWorld/>
  <EventsModifiers/>
   <ComputedProps/>
   <!-- passing props from parent to child component -->
 <ChildComponent  :message="parentMessage"/>
<NextChild :items ="itemlist"/>

  </div>
</template>

<script>
import NextChild from './components/nextChild.vue';
import ChildComponent from './components/ChildComponent.vue';
import EventsModifiers from './components/EventsModifiers.vue';
import HelloWorld from './components/HelloWorld.vue';
import ComputedProps from './components/computed.vue';
export default {
  name: 'App',
  data() {
    return {
      message: 'Hello from Vue 3!',
      isActive: false,
      count :"10",
      role: 'admin',
      isVisible: true,
      todos:['apple', 'banana', 'orange'],
      htmlContent: '<strong>This is bold HTML text</strong>',
      parentMessage: 'Hello from Parent Component', 
      itemlist: ['Item 1', 'Item 2', 'Item 3'],
    }

  },
  components: {
    HelloWorld,
    EventsModifiers,
    ComputedProps,
    ChildComponent,
    NextChild,
  },

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
.active {
  color: green;
}
</style>
