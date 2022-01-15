<template>
  <label class="radio">
    <input
      type="radio"
      class="radio__input"
      :name="getName"
      :checked="selected"
      @change="onInputChange"
    >

    <i class="radio__icon"></i>

    <div class="radio__text">
      <slot />
    </div>
  </label>
</template>

<script>
export default {
  name: 'RadioItem',

  props: {
    modelValue: { type: String },
    name: { type: String, default: '' },
    value: { type: String, default: '' },
  },
  
  inject: {
    providedName: { type: String, default: '' },
    providedValue: { type: String, default: '' },
  },

  computed: {
    selected() {
      if (typeof this.modelValue === 'string') {
        return this.value === this.modelValue
      }

      return this.providedValue.value === this.value
    },

    getName() {
      return this.name ?? this.providedName.value
    },
  },

  methods: {
    onInputChange() {
      this.$emit('update:modelValue', this.value)
      this.$parent?.onRadioChange?.(this.value)
    },
  },
}
</script>

<style>
.radio {
  display: flex;
  align-items: center;
  cursor: pointer;
}

.radio__icon {
  margin-right: 5px;

  width: 10px;
  min-width: 10px;
  height: 10px;

  background-color: #fff;
  border: 1px solid #333;
  border-radius: 50%;

}

.radio__input:checked ~ .radio__icon {
  background-color: #444;
}

.radio__input {
  display: none;
}

.radio__text {
  font-size: 15px;
}
</style>
