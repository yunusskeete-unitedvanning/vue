<template>
  <div class="home">
    Home
    <p>My name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">Click me</button>
  </div>
</template>

<script>

export default {
  name: 'HomeView',
  /*
  setup() is not reacted - if the value changes, that will not be reflected in the webpage.
  IMPORTANT: We HAVE to return variables or methods here to have them accessible inside the template.
  NOTE: We can make these reactive at a later point.
  */
  setup() {
    console.log('setup')

    let name = 'Mario'
    let age = 30

    const handleClick = () => {
      console.log('You clicked me')
    }

    return { name, age, handleClick }
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
