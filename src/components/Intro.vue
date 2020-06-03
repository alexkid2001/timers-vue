<template lang="pug">
  .intro
    .intro__wrap
      .container
        .intro__content
          .intro__logo
            img(src="/assets/img/app-icon.svg", alt="app-icon")
          .intro__title.block-title
            span AppStarter. 
            | Best landing page for web and mobile apps 
          .intro__action
            form-button(
              :mod="'button_secondary'"
            )
              | Download Now
            form-button
              | Watch Video
        .intro__tablet 
          img(src="/assets/img/tablet.png", alt="")
</template>

<script>
import FormButton from './FormButton.vue'

export default {
  components: {

  }
}
</script>

<style>

</style>
