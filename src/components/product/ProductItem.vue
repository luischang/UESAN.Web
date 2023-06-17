<template>
  <q-card class="product-card">
    <q-card-section>
      <q-img :src="product.imageUrl" alt="Imagen del producto"></q-img>
    </q-card-section>
    <q-card-section>
      <q-card-title>{{ product.description }}</q-card-title>
      <div class="text-h6 font-weigth-bold">{{ product.price }}</div>

      <div class="text-center">
        <q-btn @click="addToCart" color="primary" icon="add_shopping_cart" label="agregar"></q-btn>
      </div>
    </q-card-section>

  </q-card>
</template>

<style>
.product-card {
  width: 300px;
}

.product-card q-card-section {
  height: 100px;
  overflow: hidden;
}
</style>

<script>

import { userCartStore } from 'src/stores/cart-store';


export default {
  name: "ProductItem",
  props: {
    product: {
      type: Object,
      required: true
    }
  }, methods: {
    addToCart() {
      const store = userCartStore()
      const cart = store.totalItems
      store.addToCart(this.product)
    }
  }

}

</script>
