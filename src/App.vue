<template lang="pug">
  #app
    include components/header
    include components/intro
    Plans
    TimersBlock
    Footer
</template>

<script>
import Plans from './components/Plans.vue'
import TimersBlock from './components/TimersBlock.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'app',
  components: {
    Plans,
    TimersBlock,
    Footer,
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
}
</script>

<style>

</style>