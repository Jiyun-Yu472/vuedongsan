<template>
  <div class="black-bg" v-if="isModalOpen" @click="modalOpenSwitch()">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menuItem, menuIndex) in menus" :key="menuIndex">{{ menuItem }}</a>
  </div>
  
  <div v-for="(productItem) in products" :key="productItem.id">
    <img :src="productItem.image" class="room-img">
    <h4 @click="modalOpenSwitch()">{{ productItem.title }}</h4>
    <p>{{ productItem.price }} 원</p>
  </div>
</template>

<script>
import products from './assets/oneroom';
console.log(products);

export default {
  name: 'App',
  data() {
    return {
      products,
      menus: ['Home', 'Shop', 'About'],
      isModalOpen: false,
    }
  },
  methods: {
    increaseReportCount(productItem) {
      productItem.reportCount++;
    },
    modalOpenSwitch() {
      this.isModalOpen = !this.isModalOpen;
    }
  },
  components: {
  }
}
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
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
