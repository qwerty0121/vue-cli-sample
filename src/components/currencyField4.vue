<template>
<span class="currencyField">
  <span
    v-if="!isEdit"
    :class="['currencyField__label', {active: !isEdit}]">{{displayValue}}</span>
  <input
    type="number"
    :class="['currencyField__input', {active: isEdit}]"
    :value="value"
    @input="$emit('input', $event.target.value)"
    @blur.self="isEdit = false"
    @focus="isEdit= true">
</span>
</template>

<script>
export default {
  name: 'currencyField',
  props: ['value'],
  data () {
    return {
      isEdit: false
    }
  },
  computed: {
    displayValue () {
      return this.convertCurrency(this.value)
    }
  },
  methods: {
    convertCurrency (num) {
      num = num ? Number(num) : 0
      return `￥${num.toLocaleString()}`
    },
    clickLabel (event) {
      if (event.detail === 3) {
        return
      }
      const inputEl = event.path[1].querySelector('.currencyField__input')
      this.isEdit = true
      inputEl.focus()
      // inputEl.dispatchEvent(new MouseEvent('click', {
      //   clientX: event.pageX,
      //   clientY: event.pageY
      // }))
    }
  }
}
</script>

<style scoped>
.currencyField {
  display: flex;
  align-items: center;
  position: relative;
}
.currencyField__label {
  position: absolute;
  width: 100%;
  box-sizing: border-box;
  text-align: right;
  padding-right: 5px;
  color: transparent;
  pointer-events: none;
}
.currencyField__input {
  text-align: right;
  width: 100%;
  color: transparent;
}
.currencyField__input::-webkit-inner-spin-button,
.currencyField__input::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
    -moz-appearance:textfield;
}
.active {
  color: #000;
}
</style>
