<template lang="pug">
  label.input(:class="inputClass")
    span.input__title(
      v-if="title"
      :class="titleClass"
      ) {{title}}
    span.input__wrap(:class="wrapClass")
      input(
        :type="type"
        :name="name"
        :value="value"
        :placeholder="hint"
        @input="$emit('input', $event.target.value)"
      )
    slot
</template>

<script>
export default {
  name: 'FormInput',
  props: {
    inputClass: [String, Array],
    type: String,
    name: String,
    value: [String, Number],
    hint: String,
    title: String,
    wrapClass: String,
    titleClass: String
  }
}
</script>

<style>

</style>