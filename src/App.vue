<template>
  <div id="app" class="container">
    <button @click="scrollBackward" :disabled="currentBlock === 0" class="back-button">Назад</button>
    <div class="blocks">
      <div class="block" v-if="currentBlock === 0">
        <img src="@/img/one.jpg" alt="Изображение 1" />
      </div>
      <div class="block" v-if="currentBlock === 1">
        <img src="@/img/two.webp" alt="Изображение 1" />
      </div>
      <div class="block" v-if="currentBlock === 2">
        <img class="gif" src="@/img/three.gif" alt="Изображение 1" />
      </div>
    </div>
    <button @click="scrollForward" :disabled="currentBlock === 2" class="next-button">Далее</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentBlock: 0
    };
  },
  methods: {
    scrollForward() {
      if (this.currentBlock < 2) {
        this.currentBlock++;
      }
    },
    scrollBackward() {
      if (this.currentBlock > 0) {
        this.currentBlock--;
      }
    }
  }
};
</script>

<style>
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 auto;
  max-width: 1000px;
}

.blocks {
  display: flex;
  align-items: center;
}

.block {
  width: 200px;
  height: 200px;
  background-color: lightgray;
  text-align: center;
  line-height: 200px;
  font-size: 24px;
}

.back-button, .next-button {
  width: 150px;
  height: 50px;
  background-color: lightblue;
  text-align: center;
  line-height: 50px;
  font-size: 18px;
  margin: 0 10px;
  position: absolute;
  margin-top: 2050px;
}
.next-button{
  margin-left: 550px;
}
.gif{
  width: 1000px;
  height: 1000px;
}
</style>
