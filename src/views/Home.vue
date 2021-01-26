<template>
  <div class="home">
    <Bus msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import Bus from '@/components/Bus.vue'

export default {
  name: 'Home',
  components: {
    Bus
  }
}
</script>
