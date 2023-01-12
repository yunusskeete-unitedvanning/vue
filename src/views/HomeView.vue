<template>
  <div class="home">
    <h1>Home</h1>
    <input type="text" v-model="search">
    <p>Search term - {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">{{ name }}</div>
    <button @click="handleClick">Stop Watching</button>
  </div>
</template>

<script>
import { ref, computed, watch, watchEffect } from 'vue'
export default {
  name: 'HomeView',
  setup() {
    const search = ref('')
    const names = ref(['Mario', 'Yoshi', 'Luigi', 'Toad', 'Bowser', 'Koopa', 'Peach'])

    // Watch the search ref, and every time it changes, fire this function
    // Does not run initially
    const stopWatch = watch(search, () => {
      console.log('watch function ran')
    })

    // Runs inittially - watches any dependencies in the function and watches any value inside it.
    // Can be used to run initially to get data from the database - and then update afterwards after user input
    const stopEffect = watchEffect(() => {
      console.log('watchEffect function ran', search.value)
    })

    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value))
    })

    const handleClick = () => {
      // stops watching
      stopWatch()
      stopEffect()
    }

    return { names, search, matchingNames, handleClick }
  }
}
</script>
