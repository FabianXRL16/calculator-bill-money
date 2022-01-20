<template>
  <div class="container-m contianer">
    <h1 class="title">Monedas</h1>
    <div class="containerForm">
      <div class="itemForm">
        <span><strong>s/.</strong> 5.00</span>
        <input
          type="number"
          class="moneyInput"
          min="0"
          v-model="inputModel.m1"
        />
      </div>
      <div class="itemForm">
        <span><strong>s/.</strong> 2.00</span>
        <input
          type="number"
          class="moneyInput"
          min="0"
          v-model="inputModel.m2"
        />
      </div>
      <div class="itemForm">
        <span><strong>s/.</strong> 1.00</span>
        <input
          type="number"
          class="moneyInput"
          min="0"
          v-model="inputModel.m3"
        />
      </div>
      <div class="itemForm">
        <span><strong>s/.</strong> 0.50</span>
        <input
          type="number"
          class="moneyInput"
          min="0"
          v-model="inputModel.m4"
        />
      </div>
      <div class="itemForm">
        <span><strong>s/.</strong> 0.20</span>
        <input
          type="number"
          class="moneyInput"
          min="0"
          v-model="inputModel.m5"
        />
      </div>
      <div class="itemForm">
        <span><strong>s/.</strong> 0.10</span>
        <input
          type="number"
          class="moneyInput"
          min="0"
          v-model="inputModel.m6"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MoneyContainer",
  data() {
    return {};
  },
  props: {
    value: Object,
  },
  computed: {
    inputModel: {
      get() {
        return this.value;
      },
      set(newValue) {
        this.$emit("input", newValue);
      },
    },
  },
};
</script>

<style scoped>
.container-m {
  background: var(--bg-conatiner-sub);
  border-radius: 10px;
  grid-area: money;
}
</style>
