<template>
  <div>
    <img :src="productItem.image" class="room-img" />
    <h4 @click="modalOpenSwitchEmit(productItem)">{{ productItem.title }}</h4>
    <p>{{ productItem.price }} 원</p>
  </div>
</template>

<script>
export default {
  name: "CardProduct",
  methods: {
    modalOpenSwitchEmit(productItem) {
      this.$emit("modalOpenSwitch", productItem);
    },
  },
  props: {
    productItem: Object,
  },
};
</script>

<style></style>
