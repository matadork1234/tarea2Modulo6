<template>
    <div class="col-md-4" v-if="dataProductItem.id != itemSelected">
        <div class="card" v-on:click="selectedItem(dataProductItem.id)">
            <h5 class="card-title text-center py-3">{{ dataProductItem.nombre }}</h5>
            <img v-bind:src="dataProductItem.imagen" v-bind:alt="`image-${dataProductItem.id}`" class="w-100">
            <p class="card-text px-3">{{ dataProductItem.descripcion }}</p>
            <div class="producto-relacionado-precio">Precio:{{ dataProductItem.precio }} BOB</div>
            <div>
                <div class="text-center">
                    <div class="color-box" v-for="color in dataProductItem.colores" :key="color" v-bind:style="{ background: color }"></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'CardProduct',
        props: {
            dataProductItem: {},
            itemSelected: Number
        },
        methods: {
            selectedItem(id) {
                console.log(id);
                this.$emit('dameItem', id);
            }
        }
    }
</script>
<style scoped>
.card {
    transition: all .5s ease-in;
}

.card img {
    height: 400px;
}
.card:hover {
    transform: scale(1.05);
    cursor: pointer;
}
</style>