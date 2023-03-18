<template>
  <div class="black-bg" v-if="isModalOpen" @click="modalOpenSwitchEmit()">
    <div class="white-bg">
      <img :src="selectedProducts.image" class="room-img" />
      <h4>{{ selectedProducts.title }}</h4>
      <p>{{ selectedProducts.content }}</p>
      <input type="number" v-model="month" @click.stop />
      <p>{{ month }}개월 선택함 {{ selectedProducts.price * month }} 원</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalProduct",
  data() {
    return {
      month: 1,
    };
  },
  watch: {
    month(newValue, oldValue) {
      if (isNaN(newValue)) {
        this.month = oldValue;
      }
    },
  },
  methods: {
    modalOpenSwitchEmit() {
      this.month = 1;
      this.$emit("modalOpenSwitch");
    },
    setMonth(month) {
      this.month = month;
    },
  },
  props: {
    selectedProducts: Object,
    isModalOpen: Boolean,
  },
};
</script>

<style></style>
