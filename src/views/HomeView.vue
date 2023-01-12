<template>
  <div class="home">
    Home
    <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">Click me</button>
    <button @click="age++">Add 1 to age</button>
    <input type="text" v-model="name">
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  name: 'HomeView',
  /*
  setup() is not reacted - if the value changes, that will not be reflected in the webpage.
  IMPORTANT: We HAVE to return variables or methods here to have them accessible inside the template.
  NOTE: We can make these reactive at a later point.
  */
  setup() {
    console.log('setup')
    // this cannot be referenced here:
    console.log('this:', this)

    const p = ref(null)
    console.log('Initial p', p, p.value) // p.value will be null until returned

    // Refs are reactive values
    const name = ref('Mario')
    const age = ref(30)

    const handleClick = () => {
      console.log('You clicked me - here is p:', p, 'p.value:', p.value)
      p.value.classList.add('test')
      p.value.textContent = 'Hello, ninjas'

      name.value = 'Luigi'
      age.value = 35
    }

    return { name, age, handleClick, p }
  },
  /*
  data() is reactive - if the value changes at any point, this will be reflected in the webpage
  */
 data() {
  return {
    age: 40
  }
 }
}
</script>
