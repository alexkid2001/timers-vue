<template lang="pug">
  .timers-block
    .container.timers-block__wrap
      .block-title.timers-block__title
        span Why 
        | do we use it?
      .timers-block__discription
        | This sounded nonsense to Alice, so she said nothing, but set off at once toward the Red Queen. 
        | To her surprise, she lost sight of her in a moment.
      .timers-form
        .timers-form__create-block
          form-input(
            :inputClass="'input_timer-name'"
            :type="'text'"
            :hint="'Timer Name'"
          )
          .button.button_secondary Create Timer
        .timers-form__timers
          timer(
            :value="timer"
            :title="'Timer name 1'"
            @newTick="newTick($event)"
          )
          timer(
            :value="timer"
            :title="'Timer name 2'"
            @newTick="newTick"
          )
          timer(
            :value="timer"
            :title="'Timer name 3'"
            @newTick="newTick"
          )

</template>

<script>
import FormInput from './FormInput.vue'
import Timer from './Timer.vue'

export default {
  name: 'TimersBlock',
  components: {
    FormInput,
    Timer
  },
  data() {
    return {
      timer: '00:00:35'
    }
  },
  methods: {
    newTick(value, event) {
      console.log('newTick', value);
      console.log(event);
    }
  }
}
</script>

<style>

</style>