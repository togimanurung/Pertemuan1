<template>
  <div class="card">
    <img :src="product.image" :alt="product.name" class="product-image" />
    <h2>{{ product.name }}</h2>
    <p>Harga: Rp{{ product.price.toLocaleString() }}</p>

    <input
      v-model="buyerName"
      type="text"
      placeholder="Nama pembeli"
    />
    <input
      v-model.number="quantity"
      type="number"
      min="1"
    />

    <button @click="buyProduct">Beli</button>
    <p v-if="confirmation">{{ confirmation }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
  product: Object
});

const buyerName = ref('');
const quantity = ref(1);
const confirmation = ref('');

const buyProduct = () => {
  if (buyerName.value.trim()) {
    confirmation.value = `Terima kasih, ${buyerName.value}! Anda membeli ${quantity.value} ${props.product.name}`;
  } else {
    confirmation.value = 'Silakan masukkan nama pembeli.';
  }
};
</script>

<style scoped>
.card {
  background: #1a1a1a;
  border-radius: 10px;
  padding: 1.5rem;
  width: 300px;
  text-align: center;
  box-shadow: 0 0 10px rgba(255, 255, 255, 0.1);
}
.product-image {
  width: 100%;
  border-radius: 8px;
}
input {
  margin: 0.5rem 0.25rem;
  padding: 0.5rem;
  width: 120px;
  border: none;
  border-radius: 5px;
}
button {
  background: #00c46f;
  border: none;
  padding: 0.5rem 1rem;
  color: white;
  margin-top: 0.5rem;
  border-radius: 5px;
  cursor: pointer;
}
</style>
