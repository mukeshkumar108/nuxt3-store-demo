<template>
  <div class="container mx-auto">
    <h1 class="text-2xl font-bold mb-4">Products</h1>
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4" v-if="productList">
        <div class="border p-4" v-for="product in productList" :key="product.id">
          <h4>{{ product.title }}</h4>
          <p>${{ product.price }}</p>
        </div>
    </div>
  </div>
</template>


<script setup>
import { ref, onMounted } from '@vue/composition-api';

const productList = ref(null);

onMounted(async () => {
  const response = await fetch('https://fakestoreapi.com/products');
  productList.value = await response.json();
});

const message = ref('Initial message');

const updateMessage = () => {
  message.value = 'Message changed';
};
</script>
