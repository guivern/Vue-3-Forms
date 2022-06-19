<template>
   <input
    v-bind="$attrs"
    type="checkbox"
    :checked="modelValue"
    @change="$emit('update:modelValue', $event.target.checked)"
    class="field"
    :id="uuid"
  />
   <label v-if="label" for="uuid">{{label}}</label>
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
      type: Boolean,
      default: false
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
