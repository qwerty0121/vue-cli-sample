<template>
<input
  type="text"
  class="currency"
  v-model="innerValue">
</template>

<script>
export default {
  name: 'currencyField',
  props: ['value'],
  computed: {
    innerValue: {
      get () {
        return this.convertCurrency(this.value)
      },
      set (newVal) {
        newVal = newVal ? String(newVal) : ''
        const value = newVal.replace(/[^0-9]/g, '')
        this.$emit('input', Number(value))
        this.$forceUpdate()
      }
    }
  },
  methods: {
    convertCurrency (num) {
      num = num ? Number(num) : 0
      return `￥${num.toLocaleString()}`
    }
  }
}
</script>

<style scoped>
.currency {
  text-align: right;
}
</style>
