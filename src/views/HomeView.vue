<template>
  <div class="home">
    Home
    <p>My name is {{ name }} and my age is {{ age }}</p>
  </div>
</template>

<script>

export default {
  name: 'HomeView',
  setup() {
    console.log('setup')

    let name = 'Mario'
    let age = 30

    return { name: name, age: age }
  }
}
</script>
