<template lang="pug">
  .timer
    .timer__wrap
      .timer__title {{ title }}
      .timer__counter
        FormInput(
          :inputClass="['input_timer', isStart ? 'started': '']"
          :value="counter"
        )
      .timer__action
        form-button(
          v-if="!isStart"
          :mod="'button_success button_start'"
          @click="startTimer(true)"
        )
          svg(style="width:24px;height:24px" viewBox="0 0 24 24")
            path(d="M8,5.14V19.14L19,12.14L8,5.14Z")
        form-button(
          v-else
          :mod="'button_primary button_pause'"
          @click="stopTimer"
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
  props: ['id', 'title', 'value', 'timestamp', 'isStart' ],
  components: {
    FormInput,
    FormButton
  },
  data() {
    return {
      timerInterval: null,
      time: 0,
    }
  },
  created() {
    const date = new Date();
    if (this.isStart) {
      this.time = date.getTime() - this.timestamp;
      this.startTimer();
    } else {
      this.time = this.value;
    }
  },
  destroyed() {
    if (this.timerInterval) {
      clearInterval(this.timerInterval);
    }
  },
  computed: {
    counter() {
      const sec = parseInt(this.time / 1000, 10) ;
      let hours = parseInt((this.time / 1000 / 3600), 10);
      const minutes = ('0' + parseInt((sec - hours * 3600) / 60)).slice(-2) ;
      const seconds = ('0' + sec % 60).slice(-2);

      if (hours < 10) {
        hours = '0' +  hours;
      }
      return `${hours}:${minutes}:${seconds}`
    }
  },
  methods: {
    startTimer(needSave) {
      if (needSave) {
        this.$emit('start-timer');
      }
      this.timerInterval = setInterval(() => {
        this.time += 1000;
        }, 1000);
    },
    stopTimer() {
      clearInterval(this.timerInterval);
      this.$emit('stop-timer', {time: this.time, id: this.id});
    },
    deleteTimer() {
      this.$emit('delete-timer');
    },
  }
}
</script>

<style>

</style>