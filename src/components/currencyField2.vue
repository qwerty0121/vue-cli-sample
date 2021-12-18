<template>
<span class="currencyField">
  <span
    class="currencyField__label">￥</span>
  <input
    type="number"
    class="currencyField__input"
    :value="value"
    @input="$emit('input', $event.target.value)">
</span>
</template>

<script>
export default {
  name: 'currencyField',
  props: ['value']
}
</script>

<style scoped>
.currencyField {
  display: flex;
  align-items: center;
}
.currencyField__label {
  display: inline-block;
  background-color: #eee;
  height: 22px;
  border-radius: 5px 0px 0px 5px;
  padding: 5px;
  border-style: solid;
  border-color: #ccc;
  border-collapse: collapse;
  border-width: 1px;
  margin-right: -1px;
  width: 16px;
}
.currencyField__input {
  text-align: right;
  height: 22px;
  border-color: #ccc;
  border-style: solid;
  border-width: 1px;
  border-collapse: collapse;
  outline: none;
}
.currencyField__input::-webkit-inner-spin-button,
.currencyField__input::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
  -moz-appearance: textfield;
}
</style>
