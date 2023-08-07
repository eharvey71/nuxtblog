<script setup>
const currentCount = ref(0)

const incrementCount = () => {
  currentCount.value += 2
}
</script>

<!-- 
  - currentCount is a variable that we can use in our template, dirived from the ref() function. 
  - The ref() function is a Vue 3 function that creates a reactive variable. The 0 argument is the initial value of the variable.
  - A reactive variable is a variable that Vue keeps track of and updates the template when it changes.
  - the incrementCount function is a function that we can use in our template, and it uses a callback function to update the currentCount variable.
  - The @click attribute is a special attribute that Vue uses to add an event listener to an element.
  
-->

<template>
  <div class="counter">
    <p class="current-count">
      Current Count: <strong>{{ currentCount }}</strong>
    </p>
    <button @click="incrementCount">Add 1</button>
  </div>
</template>

<style>
.counter {
  max-width: 500px;
  padding: 15px;
  margin: 0 auto;
  border: 3px solid #ccc;
  text-align: center;
}

.counter .current-count {
  margin-bottom: 10px;
  text-align: center;
  font-size: 1.5rem;
}

.counter button {
  font-size: 1rem;
  padding: 5px;
}
</style>
