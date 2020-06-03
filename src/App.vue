<template lang="pug">
  #app
    Header
    Intro
    Plans
    TimersBlock
    Footer
</template>

<script>
import Header from './components/Header.vue'
import Intro from './components/Intro.vue'
import Plans from './components/Plans.vue'
import TimersBlock from './components/TimersBlock.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'app',
  components: {
    Header,
    Intro,
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