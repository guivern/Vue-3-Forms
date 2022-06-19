<template>
  <input
    v-bind="$attrs"
    type="radio"
    :value="value"
    :checked="value === modelValue"
    @change="$emit('update:modelValue', value)"
    :id="uuid"
  />
  <label v-if="label" :for="uuid">{{ label }}</label>
</template>

<script>
import UniqueId from '../features/UniqueID'
export default {
  props: {
    label: {
      type: String,
      default: ''
    },
    modelValue: {
      type: [String, Number, Boolean],
      default: ''
    },
    value: {
      type: [String, Number, Boolean],
      required: true
    }
  },
  setup () {
    const uuid = UniqueId().getID()
    return {
      uuid
    }
  }
}
</script>

<style>

</style>
