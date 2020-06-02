<template lang="pug">
    .timer
      .timer__wrap
        .timer__title {{ title }}
        .timer__counter
          FormInput(
            :inputClass="['input_timer', isStart ? 'started': '']"
            :value="value"
          )
        .timer__action
          form-button(
            v-if="!isStart"
            :mod="'button_success button_start'"
            @click="startTimer"
          )
            svg(style="width:24px;height:24px" viewBox="0 0 24 24")
              path(d="M8,5.14V19.14L19,12.14L8,5.14Z")
          form-button(
            v-else
            :mod="'button_primary button_pause'"
            @click="pauseTimer"
          )
            svg(style="width:24px;height:24px" viewBox="0 0 24 24")
              path(d="M14,19H18V5H14M6,19H10V5H6V19Z")
          form-button(
            :mod="'button_worning button_delete'"
            @click="deleteTimer"
          )
            svg(style="width:24px;height:24px" viewBox="0 0 24 24")
              path(d="M19,4H15.5L14.5,3H9.5L8.5,4H5V6H19M6,19A2,2 0 0,0 8,21H16A2,2 0 0,0 18,19V7H6V19Z")
</template>

<script>
import FormInput from './FormInput.vue'
import FormButton from './FormButton.vue'

export default {
  name: 'Timer',
  props: [ 'title', 'value' ],
  components: {
    FormInput,
    FormButton
  },
  data() {
    return {
      isStart: false,
      timerInterval: null,
    }
  },
  methods: {
    startTimer() {
      this.timerInterval = setInterval(() => {
        this.$emit('newTick', this.value, event)
        }, 1000);
      this.isStart = !this.isStart;
    },
    pauseTimer() {
      clearInterval(this.timerInterval);
      this.isStart = !this.isStart;
    },
    deleteTimer() {

    },
  }
}
</script>

<style>

</style>