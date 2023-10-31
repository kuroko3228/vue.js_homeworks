<template>
  <div class="block">
    <div v-for="n in 3" :key="n" class="container">
      <input v-model="newCharts[n].name" placeholder="Название" class="input_one">
      <input type="number" v-model="newCharts[n].number" placeholder="Проценты" max="100" class="input_two">
      <input v-model="newCharts[n].color" placeholder="Пиши на англ цвет" class="input-three">
      <button @click="save_btn(n)" class="save_btn">Сохранить</button>
      <div class="chart">
        <div :style="{height: charts[n].number + '%', backgroundColor: charts[n].color}"></div>
      </div>
      <div class="chart-label">
        {{ charts[n].name }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      charts: {
        1: { name: '', number: 0, color: 'yellow' },
        2: { name: '', number: 0, color: 'yellow' },
        3: { name: '', number: 0, color: 'yellow' }
      },
      newCharts: {
        1: { name: '', number: 0, color: '' },
        2: { name: '', number: 0, color: '' },
        3: { name: '', number: 0, color: '' }
      }
    };
  },
  methods: {
    save_btn(id) {
      this.charts[id].name = this.newCharts[id].name;
      this.charts[id].number = Math.min(this.newCharts[id].number, 100);
      this.charts[id].color = this.newCharts[id].color || 'yellow';
    }
  }
};
</script>

<style scoped>
.block {
  display: flex;
  justify-content: space-between;
  max-width: 960px;
  margin: 20px auto;
}
.container {
  width: 300px;
  display: inline-block;
  padding: 20px;
  border: 1px solid #000;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
.input_one, .input_two, .input-three {
  width: 100%;
  padding: 10px;
  margin-bottom: 10px;
  box-sizing: border-box;
  border: 1px solid #000;
}
.save_btn {
  width: 100%;
  padding: 10px;
  background-color: #333;
  color: #fff;
  border: none;
  cursor: pointer;
  margin-bottom: 10px;
}
.chart {
  height: 300px;
  border-top: 1px solid #000;
  position: relative;
}
.chart-label {
  text-align: center;
  padding-top: 10px;
}
</style>
