<template>
  <div class="container">
    <h1 class="title">🛍️ Daftar Produk Vape</h1>
    <div class="product-list">
      <VapeCard
        v-for="product in products"
        :key="product.id"
        :product="product"
      />
    </div>
  </div>
</template>

<script setup>
import VapeCard from '../components/VapeCard.vue';

const products = [
  {
    id: 1,
    name: 'Vape Elektrik X200',
    price: 250000,
    image: '/images/vape-x200.jpg'
  },
  {
    id: 2,
    name: 'Vape Mini Pro',
    price: 150000,
    image: '/images/vape-mini.jpg'
  }
];
</script>

<style scoped>
.container {
  padding: 2rem;
  background-color: #111;
  min-height: 100vh;
  color: white;
}
.title {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 2rem;
}
.product-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1.5rem;
}
</style>
