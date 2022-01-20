<template>
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
</template>

<script>
export default {
  name: "TotalContainer",
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
        this.total?.b1 * 200 +
          this.total?.b2 * 100 +
          this.total?.b3 * 50 +
          this.total?.b4 * 20 +
          this.total?.b5 * 10 +
          this.total?.m1 * 5 +
          this.total?.m2 * 2 +
          this.total?.m3 * 1 +
          this.total?.m4 * 0.5 +
          this.total?.m5 * 0.2 +
          this.total?.m6 * 0.1 || 0
      );
    },
  },
  props: {
    total: {
      type: Object,
      default: () => {},
    },
  },
  methods: {
    reset() {
      this.$emit("resetTotal");
    },
    print() {
      this.$emit("printCalculator");
    },
  },
};
</script>

<style scoped>
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
</style>
