<template>
    <div class="product-page">
        <div class="product-filter">

        </div>

        <div class="product-list">
            <ProductList />
        </div>
    </div>
</template>
<style>
.product-page {
    display: flex;
    justify-content: space-between;
}

.product-filter {
    width: 25%;
}

.product-list {
    width: 75%;
}
</style>
  
<script>
import { defineComponent } from 'vue'
import ProductList from 'src/components/product/ProductList.vue';

export default defineComponent({
    name: 'ProductPage',
    components: {
        ProductList
    }
})
</script>
  