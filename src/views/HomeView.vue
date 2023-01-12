<template>
  <div class="home">
    <h1>Home</h1>
    <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">Click me</button>
    <button @click="age++">Add 1 to age</button>
    <input type="text" v-model="name">
    <h2>Refs</h2>
    <p>{{ ninjaOne.name }} - {{ ninjaOne.age }}</p>
    <button @click="updateNinjaOne">Update Ninja One</button>
    <h2>Reactive</h2>
    <p>{{ ninjaTwo.name }} - {{ ninjaTwo.age }}</p>
    <button @click="updateNinjaTwo">Update Ninja Two</button>
  </div>
</template>

<script>
import { ref, reactive } from 'vue'
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
    const ninjaOne = ref({ name: 'Mario', age: 30 })
    const ninjaTwo = reactive({ name: 'Luigi', age: 35 }) // can't use primitive values with reactives. Use refs instead

    const handleClick = () => {
      console.log('You clicked me - here is p:', p, 'p.value:', p.value)
      p.value.classList.add('test')
      p.value.textContent = 'Hello, ninjas'

      name.value = 'Luigi'
      age.value = 35
    }

    const updateNinjaOne = () => {
      ninjaOne.value.age = 40
    }

    const updateNinjaTwo = () => {
      ninjaTwo.age = 45
    }

    return { name, age, handleClick, p, ninjaOne, updateNinjaOne, ninjaTwo, updateNinjaTwo }
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
