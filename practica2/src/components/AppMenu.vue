<template>
    <nav class="navbar navbar-expand-lg " :style="`background-color: ${menuColor};`">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">{{marca}}</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
                aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item">
                        <a class="nav-link" aria-current="page" :href="menus[0].url">{{menus[0].etiqueta}}</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" :href="menus[1].url">{{menus[1].etiqueta}}</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>
<script>
    export default{
        name: 'appMenu',
        data(){
            return{
                marca: "MegaDron",
                menuColor: "lightblue",
                footerColor: "slategrey",
                menus: [
                    {
                        etiqueta: "Inicio",
                        url: "www.google.com.bo"
                    },
                    {
                        etiqueta: "Tienda",
                        url: "https://es.vuejs.org/v2/guide/"
                    }
                ],
            }
        },
        props:[],
        methods: {
        }, 
        computed: {
        },
        mounted(){
        },
        components: {

        }
    }
</script>

<style></style>