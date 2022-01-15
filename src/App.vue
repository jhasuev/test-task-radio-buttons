<template>
  <div id="app">
    <radio-group
      :name="genderGroup.name"
      :label="genderGroup.label"
      :disabled="genderGroup.disabled"
      v-model="genderGroup.selected"

      class="group-item"
    >
      <radio-item
        v-for="(radio, i) in genderGroup.items"
        :key="i"
        :value="radio.value"
      >{{ radio.label }}</radio-item>
    </radio-group>

    <radio-group
      :name="interestsGroup.name"
      :label="interestsGroup.label"
      :disabled="interestsGroup.disabled"
      v-model="interestsGroup.selected"

      class="group-item"
    >
      <radio-item
        v-for="(radio, i) in interestsGroup.items"
        :key="i"
        :value="radio.value"
      >{{ radio.label }}</radio-item>
    </radio-group>

    <div class="group-item">
      <radio-item
        v-for="(radio, i) in ungrouped.radios"
        :key="`radio-${i}`"
        :value="radio.value"
        v-model="ungrouped.selected"
      >{{ radio.label }}</radio-item>
    </div>
    
    <div class="codes">
      <pre class="codes__item">genderGroup: {{ genderGroup }}</pre>
      <pre class="codes__item">interestsGroup: {{ interestsGroup }}</pre>
      <pre class="codes__item">ungrouped: {{ ungrouped }}</pre>
    </div>
  </div>
</template>

<script>
import RadioGroup from './components/RadioGroup.vue'
import RadioItem from './components/RadioItem.vue'

export default {
  name: 'App',
  components: {
    RadioGroup,
    RadioItem,
  },
  data() {
    return {
      genderGroup: {
        name: 'gender',
        label: 'Пол',
        selected: 'male',
        disabled: false,
        items: [
          {
            value: 'male',
            label: 'Мужской',
          },
          {
            value: 'female',
            label: 'Женский',
          },
          {
            value: 'no',
            label: 'Не выбрано',
          },
        ],
      },

      interestsGroup: {
        name: 'interest',
        label: 'Что вы больше всего любите делать?',
        selected: null,
        disabled: false,
        items: [
          {
            value: 'rest',
            label: 'Отдыхать',
          },
          {
            value: 'rest-and-money',
            label: 'Получать деньги',
          },
          {
            value: 'both',
            label: 'Отдыхать и получать деньги за это',
          },
        ],
      },

      ungrouped: {
        selected: 'no-groupped-1',
        radios: [
          {
            name: 'no-groupped',
            value: 'no-groupped-1',
            label: '1-ый ункт вне группы',
          },
          {
            name: 'no-groupped',
            value: 'no-groupped-2',
            label: '2-ый ункт вне группы',
          },
          {
            name: 'no-groupped',
            value: 'no-groupped-3',
            label: '3-ый ункт вне группы',
          },
        ],
      },
    }
  },
}
</script>

<style>

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: inherit;
}

body {
  font-size: 18px;
  font-family: 'Trebuchet MS';
}

#app {
  padding: 15px;
}

.group-item {
  margin-bottom: 20px;
}

.codes {
  display: inline-grid;
  grid-template-columns: 1fr 1fr 1fr;
}

.codes__item {
  font-size: 12px;
  margin-right: 15px;
}

.codes__item:last-child {
  margin-right: 0;
}

</style>
