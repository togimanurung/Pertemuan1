<template>
  <div>
    <h1>Daftar Produk Vape</h1>

    <div v-for="(vape, index) in vapes" :key="index" class="card">
      <img :src="vape.image" :alt="vape.name" />
      <h2>{{ vape.name }}</h2>
      <p>Harga: Rp{{ vape.price }}</p>

      <form @submit.prevent="beliVape(vape)">
        <input v-model="form.nama" type="text" placeholder="Nama pembeli" required />
        <input v-model.number="form.jumlah" type="number" min="1" required />
        <button :disabled="form.jumlah < 1">Beli</button>
      </form>

      <p v-if="successMessage && vape.name === lastBought" style="color: #00ffaa; margin-top: 1rem;">
        {{ successMessage }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      vapes: [
        { name: 'Vape Elektrik X200', price: 250000, image: '/src/assets/vape1.jpg' },
        { name: 'Vape Mini Pro', price: 150000, image: '/src/assets/vape2.jpg' }
      ],
      form: {
        nama: '',
        jumlah: 1
      },
      successMessage: '',
      lastBought: ''
    };
  },
  methods: {
    beliVape(vape) {
      this.successMessage = `${this.form.nama} berhasil membeli ${this.form.jumlah} ${vape.name}`;
      this.lastBought = vape.name;
      this.form.nama = '';
      this.form.jumlah = 1;
    }
  }
};
</script>
