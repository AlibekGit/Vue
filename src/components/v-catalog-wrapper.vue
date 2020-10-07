<template>
    <div class="v-catalog-wrapper">
        <router-link :to="{name: 'cart', params:{cart_data:CART}}">
            <div class="link_cart">Cart: {{CART.length}}</div>
        </router-link>

        <H1>Catalog</H1>
        <v-Catalog/>
    </div>
</template>

<script>


    import vCatalog from './v-catalog'
    import {mapGetters} from 'vuex'



    export default {
        name: "v-catalog-wrapper",

        components:{
            vCatalog
        },
        computed:{
            ...mapGetters([
                'CART'
            ])
        }

    }
</script>

<style>
    .link_cart{
        position: absolute;
        top: 10px;
        right: 10px;
        padding: 16px;
        border: solid 1px #eaeaea;
    }
        .v-catalog-wrapper{
            display: flex;
            justify-content: space-around;
            flex-direction: column;
            text-align: center;
        }
</style>