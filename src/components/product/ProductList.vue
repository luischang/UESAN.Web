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
import axios from 'axios'
import ProductItem from 'components/product/ProductItem.vue'

export default {
    name: "ProductList",
    components: {
        ProductItem
    },
    mounted() {
        this.listadoProductos()
    },
    data() {
        return {
            productos: [],
            productos1: [
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
    },
    methods: {
        listadoProductos() {
            var url = 'http://localhost:5211/api/Product'
            var token = JSON.parse(localStorage.getItem("userResult")).token
            console.log("Token: " + token)
            axios
                .get(url, {
                    headers: {
                        Authorization: 'Bearer ' + token
                    }
                })
                .then(response => {
                    console.log(JSON.stringify(response.data))
                    this.productos = response.data
                }).catch(error => {
                    this.$router.push("/")
                })

        }
    }

}

</script>