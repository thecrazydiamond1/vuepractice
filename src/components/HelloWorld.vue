<template>
<div>
<h1>{{ message }}</h1>
<p>{{ number }}</p>

<button @click="increment">Increment</button>

</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data(){
    return{
      message: 'this is helloworld component',
      number: 0,
    }
  },
  methods:{
         increment(){
          this.number++ 
         }
  }
}
</script>

