<template>
  <div class="calc">
    <div class="data">{{ data }}</div>
    <div class="result">{{ result }}</div>
    <button class="button c" @click="clear">C</button>
    <button class="button del blue" @click="setOperation('/')">÷</button>
    <button class="button" @click="appendNumber(7)">7</button>
    <button class="button" @click="appendNumber(8)">8</button>
    <button class="button" @click="appendNumber(9)">9</button>
    <button class="button blue" @click="setOperation('*')">x</button>
    <button class="button" @click="appendNumber(4)">4</button>
    <button class="button" @click="appendNumber(5)">5</button>
    <button class="button" @click="appendNumber(6)">6</button>
    <button class="button blue" @click="setOperation('-')">-</button>
    <button class="button" @click="appendNumber(1)">1</button>
    <button class="button" @click="appendNumber(2)">2</button>
    <button class="button" @click="appendNumber(3)">3</button>
    <button class="button blue" @click="setOperation('+')">+</button>
    <button class="button" @click="appendDot">.</button>
    <button class="button" @click="appendNumber(0)">0</button>
    <button class="button">space</button>
    <button class="button blue" @click="calculateResult">=</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: "",
      result: "",
      operation: null
    };
  },
  methods: {
    appendNumber(number) {
      this.data += number;
    },
    appendDot() {
      if (this.data.indexOf(".") === -1) {
        this.data += ".";
      }
    },
    setOperation(op) {
      if (this.operation === null) {
        this.operation = op;
        if (op === '÷') {
          this.data += '/';
        } else {
          this.data += op;
        }
      }
    },
    calculateResult() {
      this.result = eval(this.data);
      localStorage.setItem("result", this.result);
    },
    clear() {
      this.data = "";
      this.result = "";
      this.operation = null;
      localStorage.removeItem("result");
    }
  }
};
</script>

<style scoped>
.calc {
  width: 400px;
  height: 600px;
  margin: 0 auto;
  margin-top: 200px;
  background-color: black;
}

.button {
  width: 80px;
  height: 55px;
  margin-top: 20px;
  border: none;
  background-color: silver;
  border-radius: 24px;
  margin-left: 10px;
  font-size: 25px;
}

.blue {
  background-color: blue;
}

.data {
  color: silver;
  font-weight: 700;
  font-size: 30px;
  margin-left: 230px;
  position: absolute;
  margin-top: 50px;
}

.result {
  color: white;
  font-weight: 700;
  font-size: 30px;
  margin-left: 180px;
  margin-top: 150px;
  position: absolute;
}

.c {
  width: 150px;
  height: 55px;
  margin-left: 40px;
  margin-top: 200px;
}

.del {
  width: 150px;
  height: 55px;
}
</style>
