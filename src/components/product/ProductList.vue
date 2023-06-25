<template>
    <h6>Listado de Products</h6>
    <div class="product-list">
        <div class="product-grid">
            <div class="product-item" v-for="prod in products" :key="prod.id">
                <ProductItem :product="prod">
                </ProductItem>

            </div>
        </div>


    </div>
</template>

<style></style>

<script>

import axios from "axios"

import ProductItem from './ProductItem.vue';

export default {
    name: "ProductList",
    mounted() {
        this.cargarProductos()
    },
    components: {
        ProductItem
    },
    methods: {
        cargarProductos() {
            var url = "http://localhost:5083/api/Product"

            axios.get(url)
                .then(response => {
                    this.products = response.data
                })
        }
    },
    data() {
        return {

            productsMock: [
                {
                    "id": 1,
                    "description": "TV OLED 65 pulgadas",
                    "price": 3999,
                    "imageUrl": "https://picsum.photos/100/100"
                },
                {
                    "id": 2,
                    "description": "Iphone 23 Mega Pro",
                    "price": 14999,
                    "imageUrl": "https://picsum.photos/100/100"
                }
            ],
            products: []
        }
    }

}

</script>