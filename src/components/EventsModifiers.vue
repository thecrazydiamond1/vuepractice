<template>
    <div id="modifier-demo">
      <h2>Vue Event Modifiers Demo</h2>
  
      <!-- .prevent: prevent default form submit -->
      <form @submit.prevent="handleSubmit">
        <input v-model="name" placeholder="Enter your name" />
        <button type="submit">Submit</button>
      </form>
      <!-- .prevent is attached to the @submit event on the form.
      Normally, submitting a form reloads the page, which is the browser's default behavior.
      By using .prevent, the form’s default submit behavior (page reload) is prevented.
      The handleSubmit method will be called when the form is submitted, but the page won't refresh. -->
  
      <!-- .stop: stops event from bubbling -->
      <div @click="outerClicked" style="margin-top: 20px; border: 2px solid #ccc; padding: 20px;">
        Outer Div (click me)
  
        <button @click.stop="innerClicked">Inner Button (with .stop)</button>
      </div>
      <!-- The .stop modifier is attached to the @click event on the button inside the div.
      Normally, clicking the button would trigger the outerClicked method because events bubble up from child elements to parent elements (this is known as event bubbling).
      By adding .stop, the event is stopped from propagating to the parent div, so only the innerClicked method is called when the button is clicked.
      
      
      .once: event runs only once -->
      <button @click.once="onlyOnceClick" style="margin-top: 20px;">Click Me Only Once</button>
      <!-- .once ensures that the event handler is called only once. After the event is triggered the first time, it removes the event listener.
      In this case, when the button is clicked, the onlyOnceClick method will be executed only once. -->
     
     
      <!-- .capture: capturing phase instead of bubbling -->
      <div @click.capture="captureClick" style="margin-top: 20px; padding: 20px; border: 2px dashed teal;">
        Capture Div (click me or button inside)
        <button @click="normalClick">Inner Button (bubbles)</button>
      </div>
  <!-- You click on the button.
    The event first triggers on the parent element (div) before it reaches the button (capturing phase).
    After that, the event reaches the button itself and triggers any event handler on the button. -->
      <!-- .self: only triggers if clicked directly on the element, not children -->
       
      <div @click.self="clickedSelf" style="margin-top: 20px; background: #f3f3f3; padding: 20px;">
        Click only on this box (not its button)
        <button @click="childClick">Child Button</button>
        <!-- .self makes sure that the event is only triggered if it originates from the element itself, not from any of its child elements.
        In this case, if you click on the div itself, the clickedSelf method will be triggered. But if you click on the button inside the div, the event will not trigger the clickedSelf method. -->

        
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'EventsModifiers',
    data() {
      return {
        name: ''
      }
    },
    methods: {
      handleSubmit() {
        alert(`Form submitted by: ${this.name}`)
        this.name = ''
      },
      outerClicked() {
        alert('Outer div clicked!')
      },
      innerClicked() {
        alert('Inner button clicked! (event stopped from bubbling)')
      },
      onlyOnceClick() {
        alert('This button will not work again.')
      },
      captureClick() {
        alert('Capture phase triggered first.')
      },
      normalClick() {
        alert('Normal click (bubbling)')
      },
      clickedSelf() {
        alert('Clicked directly on the gray box!')
      },
      childClick() {
        alert('Button inside gray box clicked.')
      }
    }
  }
  </script>
  
  <style>
  #modifier-demo {
    font-family: Arial;
    padding: 30px;
  }
  </style>
  