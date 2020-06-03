<template lang="pug">
  .header
    .container.header__wrap
      .header__logo AppStarter
      .header__mobile-menu-btn(
        @click="openMobileMenu"
        v-click-outside="closeMobileMenu"
      )
        svg(style="width:24px;height:24px" viewBox="0 0 24 24")
          path(d="M3,6H21V8H3V6M3,11H21V13H3V11M3,16H21V18H3V16Z")
      .header__nav(
        :class="isMenuOpen ? 'open' : ''"
      ) 
        ul.nav
          li.nav__item Features
          li.nav__item Video Tour
          li.nav__item Reviews
          li.nav__item Pricing
        form-button(
          :mod="'button_small'"
        )
          | GET IT FREE
</template>

<script>
import FormButton from './FormButton.vue'

export default {
  data() {
    return {
      isMenuOpen: false
    }
  },
  components: {
    FormButton
  },
  methods: {
    openMobileMenu() {
      this.isMenuOpen = !this.isMenuOpen;
      this.bodyOverlay();
    },
    closeMobileMenu() {
      this.isMenuOpen = false;
      this.bodyOverlay();
    },
    bodyOverlay() {
      const body = document.querySelector('body');
      if (this.isMenuOpen) {
        body.classList.add('overlay');
      } else {
        body.classList.remove('overlay');
      }
    }

  }

}
</script>

<style>

</style>