<template>
  <div id="app" ref="app">
    <div class="container-b contianer">
      <h1 class="title">Billetes</h1>
      <div class="containerForm">
        <div class="itemForm">
          <span><strong>s/.</strong> 200</span>
          <input type="number" class="billInput" min="0" v-model="b1" />
        </div>
        <div class="itemForm">
          <span><strong>s/.</strong> 100</span>
          <input type="number" class="billInput" min="0" v-model="b2" />
        </div>
        <div class="itemForm">
          <span><strong>s/.</strong> 50</span>
          <input type="number" class="billInput" min="0" v-model="b3" />
        </div>
        <div class="itemForm">
          <span><strong>s/.</strong> 20</span>
          <input type="number" class="billInput" min="0" v-model="b4" />
        </div>
        <div class="itemForm">
          <span><strong>s/.</strong> 10</span>
          <input type="number" class="billInput" min="0" v-model="b5" />
        </div>
      </div>
    </div>
    <div class="container-m contianer">
      <h1 class="title">Monedas</h1>
      <div class="containerForm">
        <div class="itemForm">
          <span><strong>s/.</strong> 5.00</span>
          <input type="number" class="moneyInput" min="0" v-model="m1" />
        </div>
        <div class="itemForm">
          <span><strong>s/.</strong> 2.00</span>
          <input type="number" class="moneyInput" min="0" v-model="m2" />
        </div>
        <div class="itemForm">
          <span><strong>s/.</strong> 1.00</span>
          <input type="number" class="moneyInput" min="0" v-model="m3" />
        </div>
        <div class="itemForm">
          <span><strong>s/.</strong> 0.50</span>
          <input type="number" class="moneyInput" min="0" v-model="m4" />
        </div>
        <div class="itemForm">
          <span><strong>s/.</strong> 0.20</span>
          <input type="number" class="moneyInput" min="0" v-model="m5" />
        </div>
        <div class="itemForm">
          <span><strong>s/.</strong> 0.10</span>
          <input type="number" class="moneyInput" min="0" v-model="m6" />
        </div>
      </div>
    </div>
    <div class="container-t contianer">
      <h1 class="title">Total</h1>
      <div class="containerTotal">
        <span class="result"
          ><strong>s/. </strong>{{ totalPrice.toFixed(2)
          }}<span class="date"><strong>/</strong> {{ date }}</span></span
        >
        <div class="controls">
          <button class="reset" @click="reset">
            <i class="fas fa-undo-alt"></i>
          </button>
          <button class="print">
            <i class="fas fa-download" @click="print"></i>
          </button>
        </div>
      </div>
    </div>
    <img class="logo" src="./assets/logo.svg" alt="" />
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      b1: null,
      b2: null,
      b3: null,
      b4: null,
      b5: null,
      m1: null,
      m2: null,
      m3: null,
      m4: null,
      m5: null,
      m6: null,
    };
  },
  computed: {
    date() {
      let date = new Date();

      let day = date.getDate();
      let month = date.getMonth() + 1;
      let year = date.getFullYear();

      if (month < 10) {
        return `${day}/0${month}/${year}`;
      } else {
        return `${day}/${month}/${year}`;
      }
    },
    totalPrice() {
      return (
        this.b1 * 200 +
          this.b2 * 100 +
          this.b3 * 50 +
          this.b4 * 20 +
          this.b5 * 10 +
          this.m1 * 5 +
          this.m2 * 2 +
          this.m3 * 1 +
          this.m4 * 0.5 +
          this.m5 * 0.2 +
          this.m6 * 0.1 || 0
      );
    },
  },
  methods: {
    print() {
      console.log("hola");
    },
    reset() {
      this.b1 = null;
      this.b2 = null;
      this.b3 = null;
      this.b4 = null;
      this.b5 = null;
      this.m1 = null;
      this.m2 = null;
      this.m3 = null;
      this.m4 = null;
      this.m5 = null;
      this.m6 = null;
    },
  },
};
</script> 

<style>
@import url("https://fonts.googleapis.com/css2?family=Dongle:wght@300;400&display=swap");
:root {
  --bg-body: #abcffd;
  --bg-conatiner: #c0deff;
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
.container-t {
  background: var(--bg-conatiner-sub);
  border-radius: 10px;
  grid-area: total;
}
.result {
  font-size: 85px;
  line-height: 50px;
  color: var(--blue);
}
.result strong {
  font-size: 50px;
}
.containerTotal {
  display: flex;
  justify-content: space-between;
  margin-top: 5px;
}
.date {
  font-size: 30px;
  margin-left: 10px;
  font-weight: 300;
}
button {
  outline: none;
  border: none;
  cursor: pointer;
  width: 60px;
  height: 40px;
  border-radius: 10px;
  margin-left: 10px;
  color: #fff;
  font-size: 20px;
  transform: scale(1);
  transition: 0.3s;
}
button:hover {
  transform: scale(0.9);
  transition: 0.3s;
  box-shadow: rgba(99, 99, 99, 0.616) 0px 2px 8px 0px;
}
.reset {
  background: var(--green);
}
.print {
  background: var(--red);
}
@media (max-width: 750px) {
  button:hover{
    transform: scale(1);
    box-shadow: none;
  }
  .container {
    gap: 0px;
  }
  .containerTotal {
    flex-direction: column;
  }
  .result {
    font-size: 70px;
    line-height: 50px;
    color: var(--blue);
  }
  .result strong {
    font-size: 30px;
  }
  .date {
    font-size: 20px;
  }
  .controls {
    display: flex;
    justify-content: space-between;
    gap: 10px;
  }
  button {
    width: 50%;
    margin: 0;
  }
  .result {
    font-size: 65px;
    line-height: 20px;
    text-align: center;
    margin-bottom: 15px;
  }
}
.container-m {
  background: var(--bg-conatiner-sub);
  border-radius: 10px;
  grid-area: money;
}
.container-b {
  background: var(--bg-conatiner-sub);
  border-radius: 10px;
  grid-area: bill;
}
</style>
