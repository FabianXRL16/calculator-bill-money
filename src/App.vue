<template>
  <div id="app" ref="app">
    <bill v-model="total" />
    <money v-model="total" />
    <total :total="total" @resetTotal="resetPrice" @printCalculator="print" />
    <img class="logo" src="./assets/logo.svg" alt="" />
    <img :src="output" />
  </div>
</template>

<script>
import bill from "./components/billContainer.vue";
import money from "./components/moneyContainer.vue";
import total from "./components/totalContainer.vue";
export default {
  name: "App",
  components: {
    bill,
    money,
    total,
  },
  data() {
    return {
      total: {},
    };
  },
  methods: {
    resetPrice() {
      this.total = {};
    },
    print() {
      console.log("Printing...");
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Dongle:wght@300;400&display=swap");
:root {
  --bg-body: #abcffd;
  --bg-conatiner: #edf5ff;
  --bg-conatiner-sub: rgba(255, 255, 255, 0.5);
  --red: #f87171;
  --green: #34d399;
  --blue: #47a0f8;
  --gray: #63666d;
  --grayLigth: #b3b4b6;
  font-family: "Dongle", sans-serif;
}
body,
html {
  width: 100vw;
  height: 100vh;
  margin: 0;
  padding: 0px;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: center;
  background: var(--bg-body);
  position: relative;
}
#app {
  width: 700px;
  height: 500px;
  margin: 0px;
  box-sizing: border-box;
  background: var(--bg-conatiner);
  border-radius: 10px;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
  display: grid;
  grid-template-areas: "bill money" "total total";
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: 1.7fr 1fr;
  padding: 25px;
  gap: 25px;
}
.title {
  text-align: center;
  margin: 0;
  color: var(--gray);
  font-size: 40px;
  font-weight: 400;
  height: 50px;
}
.contianer {
  padding: 20px 30px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  box-sizing: border-box;
}
.containerForm {
  box-sizing: border-box;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 24px;
}
.containerForm span {
  font-size: 25px;
  color: var(--gray);
}
.itemForm {
  display: flex;
  justify-content: space-between;
  width: 105px;
}
strong {
  font-size: 15px;
}
input {
  outline: none;
  background: transparent;
  border: none;
  border-bottom: 2px var(--grayLigth) solid;
  width: 40px;
  margin-bottom: 10px;
  text-align: center;
  color: var(--gray);
  font-size: 18px;
}

input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type="number"] {
  -moz-appearance: textfield;
}
.logo {
  position: absolute;
  height: 8vw;
  bottom: 40px;
  left: 40px;
}
@media (max-width: 750px) {
  #app {
    width: 100vw;
    height: 85vh;
    grid-template-rows: 1.3fr 1fr;
    background-color: transparent;
    box-shadow: none;
    gap: 20px;
    padding: 20px;
  }
  .logo {
    display: none;
  }
}
@media (max-width: 650px) {
  #app {
    width: 100vw;
    height: 90vh;
    grid-template-rows: 2fr 1fr;
    background-color: transparent;
    box-shadow: none;
    gap: 10px;
    padding: 10px;
    margin-bottom: 10px;
  }
  .containerForm {
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 24px;
  }
}
</style>
