<template lang="pug">
  #app
    Header
    include components/intro
    Plans
    TimersBlock
    Footer
</template>

<script>
import Header from './components/Header.vue'
import Plans from './components/Plans.vue'
import TimersBlock from './components/TimersBlock.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'app',
  components: {
    Header,
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