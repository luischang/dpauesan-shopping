<template>
    <q-card class="product-card">
        <q-card-section>
            <q-img :src="product.imageUrl">
            </q-img>
        </q-card-section>
        <q-card-section>
            <q-card-title>
                {{ product.description }}
            </q-card-title>
        </q-card-section>
    </q-card>
</template>

<style></style>

<script>
export default {
    name: "ProductItem",
    props: {
        product: {
            type: Object,
            required: true
        }
    }

}

</script>