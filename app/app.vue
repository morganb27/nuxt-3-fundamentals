<script>
import { defineComponent } from '@vue/composition-api'
import TheNavBar from './components/TheNavBar.vue'

export default defineComponent({
  components: { TheNavBar },
  setup() {
    
  },
})
</script>

<template>
  <div>
    <TheNavBar />
    <NuxtPage />
  </div>
</template>
