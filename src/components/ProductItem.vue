<template>
    <div class="container">

        <div class="row">
            <h3>{{ dataProduct.nombre }}</h3>
        </div>
        <div class="row">
            <div class="col-12 col-sm-6 col-md-4 ">
                <img v-bind:src="dataProduct.imagen" v-bind:alt="`image-${ dataProduct.id }`" class="w-100">
            </div>
            <div class="col-12 col-sm-6  col-md-8">
                <h6>{{ dataProduct.descripcion }}</h6>
                <div class="p-3 mb-2 text-white" v-bind:style="stylePrice">
                    Precio: {{ dataProduct.precio }} BOB
                </div>
                <h5>Color</h5>
                <div>
                    <div class="color-box clic" v-on:click="getColor(color)" v-for="color in dataProduct.colores" :key="color"
                        v-bind:style="{ background: color }"></div>
                    <!-- <div class="color-box clic" style="background: blue"></div>
            <div class="color-box clic" style="background: black"></div> -->
                </div>
                <h5>Cantidad</h5>
                <div class="quantity">
                    <button v-on:click="reducir" v-bind:class="reducir ? 'disable' : ''">-</button>
                    <div>{{ cantidad }}</div> <button v-on:click="aumentar">+</button>
                </div>
                <div class="buy-box">
                    <button type="button" class="btn btn-primary"
                        v-bind:class="verify(cantidad, color) ? 'disabled' : ''"
                        v-on:click="comprar">Comprar</button>
                </div>

            </div>
        </div>
</div>
</template>
<script>
export default {
    name: 'ProductItem',
    props: {
        dataProduct: {},
        stylePrice: {}
    },
    data() {
        return {
            productId: 0,
            cantidad:0,
            color: ""
        }
    },
    methods: {
        getColor(color) {
            this.color = color;
            console.log(this.color);
        },
        reducir() {
            if (this.cantidad <= 0) {
                return true;
            }
            this.cantidad -= 1;
            return false
        },
        aumentar() {
            this.cantidad += 1;
        },
        verify(cantidad, color) {
            console.log(cantidad, color)
            if(this.cantidad <= 0 || this.color == "") {
                return true
            }
            return false;
        },
        comprar() {
            alert(`Producto Id = ${ this.dataProduct.id } \nCantidad = ${ this.cantidad } \nColor = ${ this.color }`)
        }
    }
}
</script>