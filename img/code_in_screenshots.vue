<!-- From the Vue Composition API RFC -->

<template>
  <button @click="increment">
    <!-- State is referenced via state.<name> -->
    Count is: {{ state.count }}, double is: {{ state.double }}
  </button>
</template>

<script>
// Import new composition api methods
import { reactive, computed } from 'vue'

export default {
  setup() {
    // reactive state (similar to Vue.observable())
    const state = reactive({
      count: 0,
      // a computed property, automatically reacting to changes in state
      double: computed(() => state.count * 2)
    })

    function increment() {
      state.count++
    }

    // explicitly return methods and state
    return {
      state,
      increment
    }
  }
}
</script>
