<template>
  <label v-if="label" for="uuid">{{label}}</label>
  <select
    :id="uuid"
    class="field"
    v-bind="$attrs"
    :value="modelValue"
    @change="$emit('update:modelValue', $event.target.value)"
    >
    <option
      v-for="option in options"
      :value="option"
      :key="option"
      :selected="option === modelValue"
    >
      {{ option }}
    </option>
  </select>
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
      type: [String, Number],
      default: ''
    },
    options: {
      type: Array,
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
