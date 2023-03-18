<template>
  <div class="discount">
    <h4>지금 결제하면 {{ discountPersent }}% 할인</h4>
  </div>
</template>

<script>
let persentInterval = "";

export default {
  name: "DiscountProduct",
  data() {
    return {
      discountPersent: 30,
    };
  },
  mounted() {
    persentInterval = setInterval(() => {
      this.discountPersent -= 1;
    }, 1000);
  },
  updated() {
    this.discountPersent == 0 ? clearInterval(persentInterval) : "";
  },
};
</script>

<style></style>
