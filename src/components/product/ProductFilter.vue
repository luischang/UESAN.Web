<template>
    <h6>Filtros</h6>
    <div class="filtro-categoria">
        <label>Categoría:</label>
        <q-select filled v-model="model" :options="categorias" label="Filled" />
        <!-- <select id="cboCategoria" class="select-filtro">
            <option value="-1">Todos</option>
            <option>Celulares</option>
            <option>Televisores</option>
            <option>Impresoras</option>
        </select> -->
    </div>
    <div class="filtro-precio">
        <label>Rango de precios:</label>
        <q-input id="precio-minimo" v-model.number="modelNumber" label="Mínimo" type="number" filled
            style="max-width: 200px" class="q-mb-xs" />
        <q-input id="precio-maximo" v-model.number="modelNumber" label="Máximo" type="number" filled
            style="max-width: 200px" />
    </div>
</template>

<style></style>

<script>
import { ref } from 'vue'
export default {
    name: "ProductFilter",
    data() {
        return {
            model: ref(null),
            modelNumber: ref(null),
            categorias: ["Celulares", "Televisores"]
            // categorias: [
            //     {
            //         "id": 1,
            //         "description": "Celulares"
            //     },
            //     {
            //         "id": 1,
            //         "description": "Televisores"
            //     }

            // ]
        }
    }

}


</script>