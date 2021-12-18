<template>
<input
  type="text"
  class="currency"
  :value="innerValue"
  @input="input($event)"
  @keydown.ctrl.z.prevent="">
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
    input (event) {
      console.log(`${this.innerValue} => ${event.target.value}`)
      const el = event.target
      const cursorPosition = el.selectionStart // 入力後のカーソル位置
      console.log(`カーソル位置: ${cursorPosition}`)
      this.innerValue = event.target.value
      this.$nextTick(() => {
        el.setSelectionRange(cursorPosition, cursorPosition)
      })
    },
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
