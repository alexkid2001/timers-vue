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
        form.timers-form__create-block(
            @submit.prevent="createTimer"
          )
            form-input(
              :inputClass="'input_timer-name'"
              :type="'text'"
              :hint="'Timer Name'"
              v-model="newTimerName"
              v-on:keyup.enter="createTimer"
            )
            .button.button_secondary(
              @click="createTimer"
            ) Create Timer
        .timers-form__timers
          timer(
            v-for="timer in timers" :key="timer.id"
            :id="timer.id"
            :value="timer.time"
            :title="timer.title"
            :timestamp="timer.timestamp"
            :isStart="timer.isStart"
            @stop-timer="stopTimer"
            @start-timer="startTimer(timer.id)"
            @delete-timer="deleteTimer(timer.id)"
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
      timer: '00:00:35',
      timers: [],
      newTimerName: '',

    }
  },
  created() {
    const storage = JSON.parse(localStorage.getItem('timers'));
    this.timers = storage ? storage : [];
    console.log('TIMERS', this.timers);
  },
  methods: {
    startTimer(id) {
      const date = new Date();
      const timer = this.timers.find(item => item.id === id);
      if (timer) {
        timer.isStart = true;
        timer.timestamp = date.getTime();
        this.saveToStorage();
      }
    },
    stopTimer(data) {
      const date = new Date();
      const index = this.timers.findIndex(item => item.id === data.id);
      
      if (index !== -1) {
        this.timers[index].isStart = false;
        this.timers[index].time = data.time;
        this.timers[index].timestamp = date.getTime();
        
        this.saveToStorage();
      }
    },
    deleteTimer(id) {
      const index = this.timers.findIndex(item => item.id === id);
      if (index >= 0 ) {
        this.timers.splice(index, 1);
        this.saveToStorage();
      }
    },
    createTimer() {
      const date = new Date();
      const month = ('0' + (date.getMonth() + 1)).slice(-2);
      const monthDay = ('0' + date.getMonth()).slice(-2);
      const name = this.newTimerName ? this.newTimerName  : `${date.getFullYear()}/${month}/${monthDay}`;
      const time = date.getTime();
      const newTimer = {
          id: time,
          title: name,
          time: 0,
          timestamp: time,
          isStart: true
        }
      this.timers.unshift(newTimer);
      this.newTimerName = '';
      this.saveToStorage();
    },
    saveToStorage() {
      localStorage.setItem('timers', JSON.stringify(this.timers));
      this.timers = JSON.parse(localStorage.getItem('timers'));
    }
  }
}
</script>

<style>

</style>