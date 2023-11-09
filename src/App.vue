<template>
  <div class="convent">
    <input type="number" min="1" v-model="amount" />
    <select v-model="selectedCurrency">
      <option value="USD">USD</option>
      <option value="EUR">EUR</option>
      <option value="RUB">RUB</option>
      <option value="AED">AED</option>
    </select>
    <p class="text">Преобразовываю</p>
    <select v-model="targetCurrency">
      <option value="USD">USD</option>
      <option value="EUR">EUR</option>
      <option value="RUB">RUB</option>
      <option value="AED">AED</option>
    </select>
    <button @click="convertCurrency">Магия</button>
    <p class="number" v-if="convertedAmount !== null">
      {{ convertedAmount.toFixed(2) }}
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      amount: 1,
      selectedCurrency: "USD",
      targetCurrency: "USD",
      exchangeRates: {
        USD: 1,
        EUR: 0.85,
        RUB: 73.5,
        AED: 3.67,
      },
      convertedAmount: null,
    };
  },
  methods: {
    convertCurrency() {
      if (this.amount && this.selectedCurrency && this.targetCurrency) {
        this.convertedAmount = (this.amount / this.exchangeRates[this.selectedCurrency]) * this.exchangeRates[this.targetCurrency];
      } else {
        this.convertedAmount = null;
      }
    },
  },
};
</script>

<style scoped>
.convent {
  width: 600px;
  margin: 0 auto;
  display: flex;
  justify-content: space-evenly;
  padding: 15px 0 0 0;
}
.text {
  color: black;
}
.number {
  color: black;
  font-weight: bold;
  margin-top: 10px;
  font-size: 20px;
}
</style>