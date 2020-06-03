<template>
  <div
    class="button"
    :class="mod"
    @click="$emit('click')"
  ><slot></slot></div>
</template>

<script>
export default {
  name: 'FormButton',
  props: {
    mod: {
      type: String,
      default: ''
    }
  }
}
</script>