<template>
  <div class="radio-group">
    <div class="radio-group__label">{{ label }}</div>
    <slot />
  </div>
</template>

<script>
import { computed } from 'vue'
export default {
  name: 'RadioGroup',

  props: {
    modelValue: { type: String, default: '' },
    name: { type: String, default: '' },
    label: { type: String, default: '' },
  },
  
  provide() {
    return {
      providedName: computed(() => this.getGroupName),
      providedValue: computed(() => this.modelValue),
    }
  },

  computed: {
    getGroupName() {
      return this.name ?? this.label
    },
  },

  methods: {
    onRadioChange(value) {
      this.$emit('update:modelValue', value)
    },
  },
}
</script>

<style>

.radio-group {
  padding: 10px;
  border: 1px solid #eee;
}
.radio-group__label {
  margin-bottom: 5px;
  font-weight: bold;
}

</style>
