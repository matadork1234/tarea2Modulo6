<template>
<nav class="navbar navbar-expand-lg" v-bind:style="{ backgroundColor: data.menuColor }" >
    <div class="container-fluid">
        <a class="navbar-brand" href="#">{{ data.marca }}</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
            data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
            aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                <li class="nav-item" v-for="menu in data.menus" :key="menu.etiqueta">
                    <a class="nav-link" aria-current="page" v-bind:href="menu.url">{{ menu.etiqueta }}</a>
                </li>
            </ul>
        </div>
    </div>
</nav>
</template>

<script>
export default {
    name: 'MenuItem',
    props: {
        data: {}
    },
    methods: {
        async dataConfig() {
            console.log(this.data)
        }
    },
    mounted() {
        this.dataConfig()
    }
}

</script>