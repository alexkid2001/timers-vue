<template lang="pug">
  .plan-block(
    :class="blockClass"
  )
    .plan-block__title {{ title }}
    .plan-block__content
      .plan-block__price {{ price }}
      .plan-block__list
        list( :items="items" )
      .plan-block__action
        .button( :class="buttonClass" ) {{buttonTitle}}

</template>

<script>
import List from "./List.vue"

export default {
  name: 'PlanBlock',
  props: {
    title: String,
    price: String,
    blockClass: String,
    items: Array,
    buttonTitle: String,
    buttonClass: String
  },
  components: {
    List
  }

}
</script>

<style>

</style>