<template>
  <div class="container-b contianer">
    <h1 class="title">Billetes</h1>
    <div class="containerForm">
      <div class="itemForm">
        <span><strong>s/.</strong> 200</span>
        <input
          type="number"
          class="billInput"
          min="0"
          v-model="inputModel.b1"
        />
      </div>
      <div class="itemForm">
        <span><strong>s/.</strong> 100</span>
        <input
          type="number"
          class="billInput"
          min="0"
          v-model="inputModel.b2"
        />
      </div>
      <div class="itemForm">
        <span><strong>s/.</strong> 50</span>
        <input
          type="number"
          class="billInput"
          min="0"
          v-model="inputModel.b3"
        />
      </div>
      <div class="itemForm">
        <span><strong>s/.</strong> 20</span>
        <input
          type="number"
          class="billInput"
          min="0"
          v-model="inputModel.b4"
        />
      </div>
      <div class="itemForm">
        <span><strong>s/.</strong> 10</span>
        <input
          type="number"
          class="billInput"
          min="0"
          v-model="inputModel.b5"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "BillContainer",
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
.container-b {
  background: var(--bg-conatiner-sub);
  border-radius: 10px;
  grid-area: bill;
}
</style>
