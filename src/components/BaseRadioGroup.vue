<template>
  <component
    v-for="option in options"
    :key="option.label"
    :is="vertical ? 'div' : 'span'"
    :class="{horizontal: !vertical}"
  >
    <base-radio
      v-bind="$attrs"
      :value="option.value"
      :label="option.label"
      :modelValue="modelValue"
      @update:modelValue="$emit('update:modelValue', option.value)"
    ></base-radio>
  </component>
</template>

<script>
export default {
  props: {
    options: {
      type: Array,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    modelValue: {
      type: [String, Number, Boolean],
      default: ''
    },
    vertical: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style scoped>
  .horizontal{margin-right: 10px;}
</style>
