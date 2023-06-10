<template>
    <h5>Listado de Productos</h5>
    <div class="product-list">
        <div class="product-grid">
            <div class="product-item" v-for="producto in productos" :key="producto.id">
                <ProductItem :product="producto"></ProductItem>
            </div>

        </div>
    </div>
</template>

<style>
.product-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 20px
}
</style>

<script>

import ProductItem from 'components/product/ProductItem.vue'

export default {
    name: "ProductList",
    components: {
        ProductItem
    },
    data() {
        return {
            productos: [
                {
                    "id": 1,
                    "description": "Samsung Galaxy 23",
                    "imageUrl": "https://picsum.photos/100/100",
                    "stock": 10,
                    "price": 3999,
                    "discount": null,
                    "category": {
                        "id": 1,
                        "description": "Celulares"
                    }
                },
                {
                    "id": 2,
                    "description": "Iphone 14",
                    "imageUrl": "https://picsum.photos/100/100",
                    "stock": 20,
                    "price": 4599,
                    "discount": null,
                    "category": {
                        "id": 1,
                        "description": "Celulares"
                    }
                }]
        }
    }

}

</script>