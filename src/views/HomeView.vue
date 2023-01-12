<template>
  <div class="home">
    Home
    <p>My name is {{ name }} and my age is {{ age }}</p>
  </div>
</template>

<script>

export default {
  name: 'HomeView',
  /*
  setup() is not reacted - if the value changes, that will not be reflected in the webpage.
  NOTE: We can make these reactive at a later point
  */
  setup() {
    console.log('setup')

    let name = 'Mario'
    let age = 30
    
    return { name: name, age: age }
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
