<template>
    <h6>Filtros</h6>
    <div class="filtro-categoria">
        <label>Categoría:</label>
        <q-select filled :options="categorias">
        </q-select>
    </div>
</template>

<style></style>

<script>

export default {
    name: "ProductFilter",
    data() {
        return {
            categorias: ["Celulares", "Televisores"]
        }
    }
}

</script>