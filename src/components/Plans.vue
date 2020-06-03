<template lang="pug">
  .plans
    .container.plans__wrap
      .plans__description
        .plans__title.block-title 
          span Choose 
          | your plan
        .plans__content This sounded nonsense to Alice, so she said nothing, but set off at once toward the Red Queen. To her surprise, she lost sight of her in a moment, and found herself walking.
        .plans__number
          form-input(
            :value="1"
            :inputClass="'input_select'"
            :type="'text'"
            :title="'Select the number of licenses:'"
          )
        .plans__promo
          form-input(
            :type="'text'"
            :title="'Enter the promo code:'"
            :hint="'Promo code'"
          )
          .button.button_small.button_primary Apply
      .plans__list
        plan-block(
          :title="'Professional'"
          :price="'10$'"
          :blockClass="'plan-block_primary'"
          :items=[
              'Hundreds of elements',
              'Style guide',
              '160 icons included',
              'Sketch files',
              'Commercial licence'
            ]
          :buttonTitle="'Buy Now'"
          :buttonClass="'button_secondary'"
        )
        plan-block(
          :title="'STARTER'"
          :price="'FREE'"
          :items=[
              'Hundreds of elements',
              'Style guide',
              '30 icons included',
              'Personal licence'
            ]
          :buttonTitle="'Get Free'"
          :buttonClass="'button_success'"
        )
  
</template>

<script>

import FormInput from './FormInput.vue'
import PlanBlock from './PlanBlock.vue'

export default {
  name: "Plans",
  components: {
    FormInput,
    PlanBlock
  }

}
</script>

<style>

</style>

