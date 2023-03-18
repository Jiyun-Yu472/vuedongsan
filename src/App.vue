<template>
  <transition name="fade">
    <ModalProduct
      :selectedProducts="selectedProducts"
      :isModalOpen="isModalOpen"
      @modalOpenSwitch="modalOpenSwitch"
    />
  </transition>

  <div class="menu">
    <a v-for="(menuItem, menuIndex) in menus" :key="menuIndex">{{
      menuItem
    }}</a>
  </div>

  <DiscountProduct />

  <button @click="priceSort()">가격순 정렬</button>
  <button @click="pricReverseSort()">가격역순 정렬</button>
  <button @click="hangulSort()">가나다순 정렬</button>
  <button @click="sortBack()">정렬 되돌리기</button>

  <CardProduct
    v-for="productItem in products"
    :key="productItem.id"
    :productItem="productItem"
    @modalOpenSwitch="modalOpenSwitch"
  />
</template>

<script>
import products from "./assets/oneroom";
import DiscountProduct from "./components/DiscountProduct.vue";
import ModalProduct from "./components/ModalProduct.vue";
import CardProduct from "./components/CardProduct.vue";

export default {
  name: "App",
  data() {
    return {
      originProducts: [...products],
      products,
      menus: ["Home", "Shop", "About"],
      isModalOpen: false,
      selectedProducts: {},
    };
  },
  methods: {
    increaseReportCount(productItem) {
      productItem.reportCount++;
    },
    modalOpenSwitch(productItem = null) {
      this.selectedProducts = productItem;
      this.isModalOpen = !this.isModalOpen;
    },
    priceSort() {
      this.products.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    pricReverseSort() {
      this.products.sort(function (a, b) {
        return b.price - a.price;
      });
    },
    hangulSort() {
      this.products.sort(function (a, b) {
        return a.title.localeCompare(b.title);
      });
    },
    sortBack() {
      this.products = [...this.originProducts];
    },
  },
  components: {
    DiscountProduct,
    ModalProduct,
    CardProduct,
  },
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}

.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: 1s;
}
.fade-enter-to {
  opacity: 1;
}
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: 1s;
}
.fade-leave-to {
  opacity: 0;
}
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
