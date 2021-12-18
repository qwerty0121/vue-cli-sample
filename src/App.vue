<template>
  <div id="app" class="abc">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <div class="field">
      <span class="label">computedでフォーマット</span>
      <currency-field v-model="currency" class="inputArea" />
    </div>
    <div class="field">
      <span class="label">￥をラベルとして表示(カンマ区切りなし)</span>
      <currency-field2 v-model="currency" class="inputArea" />
    </div>
    <div class="field">
      <span class="label">computedでフォーマット(カーソル位置を制御)</span>
      <currency-field3 v-model="currency" class="inputArea" />
    </div>
    <div class="field">
      <span class="label">入力時はinput、それ以外はラベル表示</span>
      <currency-field4 v-model="currency" class="inputArea" />
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import CurrencyField from '@/components/currencyField'
import CurrencyField2 from '@/components/currencyField2'
import CurrencyField3 from '@/components/currencyField3'
import CurrencyField4 from '@/components/currencyField4'

export default {
  name: 'App',
  components: {
    // HelloWorld
    CurrencyField,
    CurrencyField2,
    CurrencyField3,
    CurrencyField4
  },
  data () {
    return {
      currency: 0
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 20px;
  width: 80vw;
  margin: 0 auto;
}
input {
  padding: 5px;
  font-size: 1rem;
}
.field {
  display: grid;
  grid-template-columns: 400px 200px;
}
.label {
  text-align: left;
}
</style>
